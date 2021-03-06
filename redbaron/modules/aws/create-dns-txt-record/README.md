# create-dns-txt-record

Adds records to a domain using AWS Route53

# Example

```hcl
module "create_a_record" {
  source = "./modules/aws/create-dns-record"

  type = "TXT"
  name = ""
  records = {
    "domain.com" = "192.168.0.1"
    "test.domain.com" = "192.168.0.2"
  }
  zone = "zoneID"
}
```

# Arguments

| Name                      | Required | Value Type | Description
|---------------------------| -------- | ---------- | -----------
|`type`                     | Yes      | String     | The record type to add. Valid values are A, AAAA, CAA, CNAME, MX, NAPTR, NS, PTR, SOA, SPF, SRV and TXT.
|`records`                  | Yes      | Map        | A map of records to add. Domains as keys and IPs as values.
|`zone`                     | Yes      | String     | AWS ZoneID of the Route53 for that domain
|`name`                     | Yes      | String     | Use @ to create the record at the root of the domain or enter a hostname to create it elsewhere. A records are for IPv4 addresses only and tell a request where your domain should direct to.
|`ttl`                      | No       | Integer    | The TTL of the record(s). Default value is 300

# Outputs

| Name                      | Value Type | Description
|---------------------------| ---------- | -----------
|`records`                  | Map        | Map containing the records added to the domain. Domains as keys and IPs as values.

