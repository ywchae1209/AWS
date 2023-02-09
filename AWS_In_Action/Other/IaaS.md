## < IaaS >

---

1. Overall

   - Tenant
   - Region
   - Avaiability Zone

2. Network resource

   - Virtual Router : VPC, EIP
   - Virtaul switch / Subnet
   - IP Masquerading / ElasticIP ( Floating IP)
   - Security Group ( Packet Filtering )

3. Server resource

   - Template Image
   - Instance Type : CPU /Memory / Ephemeral disk ( Root disk/ temp disk) vs ( EBS, S3)
   - Network access : Instance + Virtual NIC + security group + virtual switch
   - login & key-pair : Cloud-init

4. Block storage

   - Block Storage
   - EBS Boot ( Boot from volume )

5. Object stroage

   - Object Stroage
   - Bucket ( Object container )
   - Versioning & Static web hosting
   - backup Block storage using Object storage

6. Simple web hosting

   - multiple AZ : Fail-over // DNS or Load-Balancer
   - object storage : EBS --> snapshot --> S3 backup // using RBD's replication function ( with EBS )

## < API >

---

1. Cloud & API

   - API
   - Web API
     | ex: product Advertising API (Amazon)

   - SOA ( Service Oriented Architecture ; 2000's), SoE ( System of Engagement )
   - Actor( Authentication ) / Resource (URI) / Action / Condition
   - Resource : UUID, name

2. Resource, URI

   - URI : name/location or both ~ scheme + authority + path + query

     > scheme:[//authority = user:pwd@www.abc.com/]path[?query][#fragment]

   - URL : location ~ authority = domain name + port
   - URN : name ~ urn:isbn(Namespace ID):0012345(Namespace specific string)

     > arn:aws:ec2:ap-korea:acccount-id:instance-type/instance-id

   - FQDN, TLD, 2ndLD, ...
   - DNS : 1:N (DNS round-robin), N:1 (virtual hosting)

## VPC configuration

- VPC : 10.0.0.0/16

  > Name : VPC_ID : Status : CIDR  
  > DNS

  - Routing table

    - local routing : routing between subnets in a VPC
    - Gateway routing table
      - IGW : Internet Gateway
      - PCX : Peer connection
      - VPG : Virtual Private Gateway
      - Nat GW : NAT Gateway

EIP
NAT Gateway
VPC Endpoint

| name     | example     | etc  |
| -------- | ----------- | ---- |
| subnet-1 | 10.0.1.0/24 | AZ-1 |
| subnet-2 | 10.0.2.0/24 | AZ-2 |
| subnet-3 | 10.0.3.0/24 | AZ-3 |
| subnet-4 | 10.0.4.0/24 | AZ-4 |
| ...      | ...         | ...  |

- subnet-1
  > Name : Subnet_ID : status : VPC : CIDR : ...
  > Routing table, NACL, DHCP,

| IP         | usage                                     |
| ---------- | ----------------------------------------- |
| 10.0.1.0   | Network ID                                |
| 10.0.1.1   | Defalt G/W, Router                        |
| 10.0.1.2   | DNS server IP                             |
| 10.0.1.3   | Reserved                                  |
| 10.0.1.255 | Reserved (Broadcast : non-allowed in VPC) |

- Routing table
