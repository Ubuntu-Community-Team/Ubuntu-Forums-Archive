---
title: "New Install on RPi5  Network error on connection to canonical &quot;Network unreachable&quot;"
date: 2024-10-13
forum: Networking &amp; Wireless
---

### Post by doug-ravennasprings on 2024-10-13
On a brand new installation of Ubuntu on a Raspberry Pi, my firewall/proxy system is logging errors suggesting that the IPv6 configuration is misconfigured.
At least that's my best guess.  This looks like a (very) basic configuration error that would affect all versions of Ubuntu, perhaps globally.  What the carbon footprint of the increased logs world-wide?

Here are the errors:
httpproxy[20938]: id="0003" severity="info" sys="SecureWeb" sub="http"  request="0x110f2000" function="connect_server" file="dns.c" line="1288"  message="connect() on AF 10 socket to 2620:2d:4002:1::197 failed:  Network is unreachable

Here's what I find when I lookup this address:

**Address lookup**

 [TABLE]
[TR]
[TD]canonical name[/TD]
[TD][aerodent]("http://www.aerodent.canonical.com/").[canonical.com]("http://www.canonical.com/").[/TD]
[/TR]
[TR]
[TD]aliases[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]addresses[/TD]
[TD] 2620:2d:4000:1::19[/TD]
[/TR]
[/TABLE]
                   **Domain Whois record**

  Queried whois.internic.net with "dom canonical.com"...
    Domain Name: CANONICAL.COM
   Registry Domain ID: 34100_DOMAIN_COM-VRSN
   Registrar WHOIS Server: whois.markmonitor.com
   Registrar URL: [http://www.markmonitor.com](http://www.markmonitor.com)
   Updated Date: 2023-08-30T22:38:58Z
   Creation Date: 1996-07-05T04:00:00Z
   Registry Expiry Date: 2025-07-04T04:00:00Z
   Registrar: MarkMonitor Inc.
   Registrar IANA ID: 292
   Registrar Abuse Contact Email: [EMAIL="abusecomplaints@markmonitor.com"]abusecomplaints@markmonitor.com[/EMAIL]
   Registrar Abuse Contact Phone: +1.2086851750
   Domain Status: clientDeleteProhibited [https://icann.org/epp#clientDeleteProhibited](https://icann.org/epp#clientDeleteProhibited)
   Domain Status: clientTransferProhibited [https://icann.org/epp#clientTransferProhibited](https://icann.org/epp#clientTransferProhibited)
   Domain Status: clientUpdateProhibited [https://icann.org/epp#clientUpdateProhibited](https://icann.org/epp#clientUpdateProhibited)
   Name Server: NS1.CANONICAL.COM
   Name Server: NS2.CANONICAL.COM
   Name Server: NS3.CANONICAL.COM
   DNSSEC: unsigned
   URL of the ICANN Whois Inaccuracy Complaint Form: [https://www.icann.org/wicf/](https://www.icann.org/wicf/)
>>> Last update of whois database: 2024-10-13T22:35:32Z <<<
Queried whois.markmonitor.com with "canonical.com"...
 Domain Name: canonical.com
Registry Domain ID: 34100_DOMAIN_COM-VRSN
Registrar WHOIS Server: whois.markmonitor.com
Registrar URL: [http://www.markmonitor.com](http://www.markmonitor.com)
Updated Date: 2024-08-02T02:17:33+0000
Creation Date: 1996-07-05T04:00:00+0000
Registrar Registration Expiration Date: 2025-07-04T00:00:00+0000
Registrar: MarkMonitor, Inc.
Registrar IANA ID: 292
Registrar Abuse Contact Email: [EMAIL="abusecomplaints@markmonitor.com"]abusecomplaints@markmonitor.com[/EMAIL]
Registrar Abuse Contact Phone: +1.2086851750
Domain Status: clientUpdateProhibited ([https://www.icann.org/epp#clientUpdateProhibited](https://www.icann.org/epp#clientUpdateProhibited))
Domain Status: clientTransferProhibited ([https://www.icann.org/epp#clientTransferProhibited](https://www.icann.org/epp#clientTransferProhibited))
Domain Status: clientDeleteProhibited ([https://www.icann.org/epp#clientDeleteProhibited](https://www.icann.org/epp#clientDeleteProhibited))
Registrant Organization: Canonical, Ltd.
Registrant State/Province: Isle of Man
Registrant Country: GB
Registrant Email: Select Request Email Form at [https://domains.markmonitor.com/whois/canonical.com](https://domains.markmonitor.com/whois/canonical.com)
Admin Organization: Canonical, Ltd.
Admin State/Province: Isle of Man
Admin Country: GB
Admin Email: Select Request Email Form at [https://domains.markmonitor.com/whois/canonical.com](https://domains.markmonitor.com/whois/canonical.com)
Tech Organization: Canonical, Ltd.
Tech State/Province: Isle of Man
Tech Country: GB
Tech Email: Select Request Email Form at [https://domains.markmonitor.com/whois/canonical.com](https://domains.markmonitor.com/whois/canonical.com)
Name Server: ns3.canonical.com
Name Server: ns1.canonical.com
Name Server: ns2.canonical.com
DNSSEC: unsigned
URL of the ICANN WHOIS Data Problem Reporting System: [http://wdprs.internic.net/](http://wdprs.internic.net/)
>>> Last update of WHOIS database: 2024-10-13T22:33:10+0000 <<<
         **Network Whois record**

 Queried whois.arin.net with "n 2620:2d:4000:1::19"...
 NetRange:       2620:2D:4000:: - 2620:2D:400F:FFFF:FFFF:FFFF:FFFF:FFFF
CIDR:           2620:2D:4000::/44
NetName:        CANONICAL-USA6
NetHandle:      NET6-2620-2D-4000-1
Parent:         ARIN-V6-ENDUSER-BLOCK (NET6-2620-1)
NetType:        Direct Allocation
OriginAS:       AS41231
Organization:   Canonical USA Inc. (CU-17)
RegDate:        2013-06-04
Updated:        2021-12-14
Comment:        [http://www.canonical.com/](http://www.canonical.com/)
Ref:            [https://rdap.arin.net/registry/ip/2620:2D:4000::](https://rdap.arin.net/registry/ip/2620:2D:4000::)


OrgName:        Canonical USA Inc.
OrgId:          CU-17
Address:        720 Brazos Street, Suite 300
City:           Austin
StateProv:      TX
PostalCode:     78701
Country:        US
RegDate:        2012-04-10
Updated:        2023-08-10
Ref:            [https://rdap.arin.net/registry/entity/CU-17](https://rdap.arin.net/registry/entity/CU-17)


OrgTechHandle: CANON4-ARIN
OrgTechName:   Canonical IS
OrgTechPhone:  +1-781-761-9400 
OrgTechEmail:  [EMAIL="hostmaster@canonical.com"]hostmaster@canonical.com[/EMAIL]
OrgTechRef:    [https://rdap.arin.net/registry/entity/CANON4-ARIN](https://rdap.arin.net/registry/entity/CANON4-ARIN)

OrgAbuseHandle: CANON-ARIN
OrgAbuseName:   Canonical Abuse
OrgAbusePhone:  +1-781-761-9400 
OrgAbuseEmail:  [EMAIL="abuse@canonical.com"]abuse@canonical.com[/EMAIL]
OrgAbuseRef:    [https://rdap.arin.net/registry/entity/CANON-ARIN](https://rdap.arin.net/registry/entity/CANON-ARIN)

OrgNOCHandle: CANON1-ARIN
OrgNOCName:   Canonical NOC
OrgNOCPhone:  +1-781-761-9400 
OrgNOCEmail:  [EMAIL="noc@canonical.com"]noc@canonical.com[/EMAIL]
OrgNOCRef:    [https://rdap.arin.net/registry/entity/CANON1-ARIN](https://rdap.arin.net/registry/entity/CANON1-ARIN)
         **DNS records**

  [TABLE]
[TR]
[TD="class: hdr"]name[/TD]
[TD="class: hdr"]class[/TD]
[TD="class: hdr"]type[/TD]
[TD="class: hdr"]data[/TD]
[TD="class: hdr, colspan: 2"]time to live[/TD]
[/TR]
[TR]
[TD]aerodent.canonical.com[/TD]
[TD]IN[/TD]
[TD]AAAA[/TD]
[TD]2620:2d:4000:1::19[/TD]
[TD]1800s[/TD]
[TD](00:30:00)[/TD]
[/TR]
[TR]
[TD]aerodent.canonical.com[/TD]
[TD]IN[/TD]
[TD]A[/TD]
[TD]185.125.190.39[/TD]
[TD]1800s[/TD]
[TD](00:30:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]SOA[/TD]
[TD][TABLE]
[TR]
[TD="class: hdr"]server:[/TD]
[TD]ns1.canonical.com[/TD]
[/TR]
[TR]
[TD="class: hdr"]email:[/TD]
[TD]hostmaster@canonical.com[/TD]
[/TR]
[TR]
[TD="class: hdr"]serial:[/TD]
[TD]2018063071[/TD]
[/TR]
[TR]
[TD="class: hdr"]refresh:[/TD]
[TD]10800[/TD]
[/TR]
[TR]
[TD="class: hdr"]retry:[/TD]
[TD]3600[/TD]
[/TR]
[TR]
[TD="class: hdr"]expire:[/TD]
[TD]604800[/TD]
[/TR]
[TR]
[TD="class: hdr"]minimum ttl:[/TD]
[TD]3600[/TD]
[/TR]
[/TABLE]
[/TD]
[TD]3600s[/TD]
[TD](01:00:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]NS[/TD]
[TD]ns1.canonical.com[/TD]
[TD]172800s[/TD]
[TD](2.00:00:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]NS[/TD]
[TD]ns3.canonical.com[/TD]
[TD]172800s[/TD]
[TD](2.00:00:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]NS[/TD]
[TD]ns2.canonical.com[/TD]
[TD]172800s[/TD]
[TD](2.00:00:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]TXT[/TD]
[TD]miro-verification=2a474c203a12d0d3bdedb1dbfd7df2350d60c43d[/TD]
[TD]600s[/TD]
[TD](00:10:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]TXT[/TD]
[TD]bw=FUPOteh4WFoKj2FJCprEWcFcZYwSQOSwgn2njwUTAlAn[/TD]
[TD]600s[/TD]
[TD](00:10:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]TXT[/TD]
[TD]apple-domain-verification=p5U0KoYntPjPy6ah[/TD]
[TD]600s[/TD]
[TD](00:10:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]TXT[/TD]
[TD]atlassian-domain-verification=EfMI3zSzpIoFk2/QhOqWVwC3swzqP9UryHYJFB0SyITHLVntyXkupk6prHjka48F[/TD]
[TD]600s[/TD]
[TD](00:10:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]TXT[/TD]
[TD]google-site-verification=RFZCSssfnIjPnBo0k6W72VsUfYqbknSNqIgy2TrcMms[/TD]
[TD]600s[/TD]
[TD](00:10:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]TXT[/TD]
[TD]v=spf1 include:_spf.canonical.com -all[/TD]
[TD]600s[/TD]
[TD](00:10:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]TXT[/TD]
[TD]google-site-verification=987aj5PIoVpH3ybA_tMmNcCZ7sY64IUEGaeafo_hrFk[/TD]
[TD]600s[/TD]
[TD](00:10:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]MX[/TD]
[TD][TABLE]
[TR]
[TD="class: hdr"]preference:[/TD]
[TD]10[/TD]
[/TR]
[TR]
[TD="class: hdr"]exchange:[/TD]
[TD]mx.canonical.com[/TD]
[/TR]
[/TABLE]
[/TD]
[TD]600s[/TD]
[TD](00:10:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]AAAA[/TD]
[TD]2620:2d:4000:1::28[/TD]
[TD]60s[/TD]
[TD](00:01:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]AAAA[/TD]
[TD]2620:2d:4000:1::27[/TD]
[TD]60s[/TD]
[TD](00:01:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]AAAA[/TD]
[TD]2620:2d:4000:1::26[/TD]
[TD]60s[/TD]
[TD](00:01:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]A[/TD]
[TD]185.125.190.29[/TD]
[TD]60s[/TD]
[TD](00:01:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]A[/TD]
[TD]185.125.190.20[/TD]
[TD]60s[/TD]
[TD](00:01:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]A[/TD]
[TD]185.125.190.21[/TD]
[TD]60s[/TD]
[TD](00:01:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]CAA[/TD]
[TD][TABLE]
[TR]
[TD="class: hdr"][no interpretation available]
hex dump:
(36 bytes)[/TD]
[TD]00 05 69 6F 64 65 66 6D  ..iodefm
61 69 6C 74 6F 3A 69 73  ailto:is
2D 61 64 6D 69 6E 40 63  -admin@c
61 6E 6F 6E 69 63 61 6C  anonical
2E 63 6F 6D              .com[/TD]
[/TR]
[/TABLE]
[/TD]
[TD]3600s[/TD]
[TD](01:00:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]CAA[/TD]
[TD][TABLE]
[TR]
[TD="class: hdr"][no interpretation available]
hex dump:
(23 bytes)[/TD]
[TD]00 09 69 73 73 75 65 77  ..issuew
69 6C 64 64 69 67 69 63  ilddigic
65 72 74 2E 63 6F 6D     ert.com[/TD]
[/TR]
[/TABLE]
[/TD]
[TD]3600s[/TD]
[TD](01:00:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]CAA[/TD]
[TD][TABLE]
[TR]
[TD="class: hdr"][no interpretation available]
hex dump:
(19 bytes)[/TD]
[TD]00 05 69 73 73 75 65 64  ..issued
69 67 69 63 65 72 74 2E  igicert.
63 6F 6D                 com[/TD]
[/TR]
[/TABLE]
[/TD]
[TD]3600s[/TD]
[TD](01:00:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]CAA[/TD]
[TD][TABLE]
[TR]
[TD="class: hdr"][no interpretation available]
hex dump:
(89 bytes)[/TD]
[TD]00 05 69 73 73 75 65 6C  ..issuel
65 74 73 65 6E 63 72 79  etsencry
70 74 2E 6F 72 67 3B 20  pt.org; 
61 63 63 6F 75 6E 74 75  accountu
72 69 3D 68 74 74 70 73  ri=https
3A 2F 2F 61 63 6D 65 2D  ://acme-
76 30 31 2E 61 70 69 2E  v01.api.
6C 65 74 73 65 6E 63 72  letsencr
79 70 74 2E 6F 72 67 2F  ypt.org/
61 63 6D 65 2F 72 65 67  acme/reg
2F 33 32 35 34 31 32 39  /3254129
30                       0[/TD]
[/TR]
[/TABLE]
[/TD]
[TD]3600s[/TD]
[TD](01:00:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]CAA[/TD]
[TD][TABLE]
[TR]
[TD="class: hdr"][no interpretation available]
hex dump:
(22 bytes)[/TD]
[TD]00 05 69 73 73 75 65 6C  ..issuel
65 74 73 65 6E 63 72 79  etsencry
70 74 2E 6F 72 67        pt.org[/TD]
[/TR]
[/TABLE]
[/TD]
[TD]3600s[/TD]
[TD](01:00:00)[/TD]
[/TR]
[TR]
[TD]canonical.com[/TD]
[TD]IN[/TD]
[TD]CAA[/TD]
[TD][TABLE]
[TR]
[TD="class: hdr"][no interpretation available]
hex dump:
(26 bytes)[/TD]
[TD]00 09 69 73 73 75 65 77  ..issuew
69 6C 64 6C 65 74 73 65  ildletse
6E 63 72 79 70 74 2E 6F  ncrypt.o
72 67                    rg[/TD]
[/TR]
[/TABLE]
[/TD]
[TD]3600s[/TD]
[TD](01:00:00)[/TD]
[/TR]
[TR]
[TD]9.1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.1.0.0.0.0.0.0.4.d.2.0.0.0.2.6.2.ip6.arpa[/TD]
[TD]IN[/TD]
[TD]PTR[/TD]
[TD]aerodent.canonical.com[/TD]
[TD]3600s[/TD]
[TD](01:00:00)[/TD]
[/TR]
[TR]
[TD]1.0.0.0.0.0.0.4.d.2.0.0.0.2.6.2.ip6.arpa[/TD]
[TD]IN[/TD]
[TD]SOA[/TD]
[TD][TABLE]
[TR]
[TD="class: hdr"]server:[/TD]
[TD]ns1.canonical.com[/TD]
[/TR]
[TR]
[TD="class: hdr"]email:[/TD]
[TD]hostmaster@canonical.com[/TD]
[/TR]
[TR]
[TD="class: hdr"]serial:[/TD]
[TD]28[/TD]
[/TR]
[TR]
[TD="class: hdr"]refresh:[/TD]
[TD]10800[/TD]
[/TR]
[TR]
[TD="class: hdr"]retry:[/TD]
[TD]3600[/TD]
[/TR]
[TR]
[TD="class: hdr"]expire:[/TD]
[TD]604800[/TD]
[/TR]
[TR]
[TD="class: hdr"]minimum ttl:[/TD]
[TD]3600[/TD]
[/TR]
[/TABLE]
[/TD]
[TD]3600s[/TD]
[TD](01:00:00)[/TD]
[/TR]
[TR]
[TD]1.0.0.0.0.0.0.4.d.2.0.0.0.2.6.2.ip6.arpa[/TD]
[TD]IN[/TD]
[TD]NS[/TD]
[TD]ns1.canonical.com[/TD]
[TD]3600s[/TD]
[TD](01:00:00)[/TD]
[/TR]
[TR]
[TD]1.0.0.0.0.0.0.4.d.2.0.0.0.2.6.2.ip6.arpa[/TD]
[TD]IN[/TD]
[TD]NS[/TD]
[TD]ns3.canonical.com[/TD]
[TD]3600s[/TD]
[TD](01:00:00)[/TD]
[/TR]
[TR]
[TD]1.0.0.0.0.0.0.4.d.2.0.0.0.2.6.2.ip6.arpa[/TD]
[TD]IN[/TD]
[TD]NS[/TD]
[TD]ns2.canonical.com[/TD]
[TD]3600s[/TD]
[TD](01:00:00)[/TD]
[/TR]
[/TABLE]

---

### Post by doug-ravennasprings on 2024-10-13
This appears to be an error in how Ubuntu is attempting to accessing updates.
Is this not tested, before release?

Typing the address into a browser gets a successful connection with the following result:

[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAgIAAAEnCAYAAADbzCvUAAAgAElEQVR4Xu2deWDUxfn/nw2VpggoCMopKIdBymGlIIpaK6IiEVoJVETk1spp5SzKkaQBBCEo gXLfVhBIipUFPCkKoT6q7UcKgVBDgsioiBiIMlvn93M7uxkPsdudrObzHv/UbKfz8w8r5nP53nPPM/MegoLCgsJHxAAARAAARAAASMJeCAEjOx3GA0CIAACIAACPgIQAhgIIAACIAACIGAwAQgBgzsfpoMACIAACIAAhADGAAiAAAiAAAgYTABCwODOh kgAAIgAAIgACGAMQACIAACIAACBhOAEDC482E6CIAACIAACEAIYAyAAAiAAAiAgMEEIAQM7nyYDgIgAAIgAAIhQuBoTluqlbbdFZUUmkDrCzKpkaurS3ZRnieb7qwyht46fa5YQR3arKItuT1KVkEZvPt8/n56/dlxNPGZt mLw8fo5A9EFZOrU8P6nSjr aV0z7UVw7Lq8Ibf0i 7vk31K2bRhtPjqW5Yd NiEAABEACBskpAuyJw/PBz1O/mB2n9vlCzKtJl1HfSmzRjXHOq vPSN/l//x1Kt1/7DH1yKli3iULgm/1Z9PubJtN7h85RZWpG097dSTf950pqOXS/D8zF1I7m7thK913tvo WDPBQv8VEDww9REueggxwTw5XggAIgEDZJmAZGngn00O3TAw1rjRXAXRYz3u20tAW7Wn DnOFwE e56lnvfvolcN BrWoGz2fv5aufil0NafX4L20ct6VrkZnnmcl9ajdm97537X01I5/Up8wBISrCnARCIAACIBAwhKwFAK6MAGEQPz78bMlV9M1/XfTj0VNEUKg boO1LDb 4G/93/kKC188lJXDf56cydq2nkT1TpfeuEeVw3DRSAAAiAAAjEnACEQc8TRrWDTJA91ygiWKYRAB88W tP1N9HCrZWo VVTaPnHoyjFZfhGhAV69NtNqxamRLfBKA0EQAAEQCChCUAIJHT3FG clRC4xROZIec86 mBK1Jp3f5mNPODXfTgdZGVg7tAAARAAATKJgEIgTLWb9EWAt9svYd edNLdDHCAmVsJKC5IAACIBAdAiUWAlZbDjmb/73tnekfi/vRiMxN9Om 7yjfu72tZYuHaPaqdOrQsIKlBcc W0jpY2fSC 9 St98R3RR1Ssp9d6FNGteMj0eRrKgKGfNP/bT0RNnfdvrrmryO5q06NmQ7XV22xO5kSO92Yk/Pv3LkCRF0fjxswopa2R4nZGX9/9oUfpoenr5J/TlweN02nt71Ytr05X1O9OwaROp152XU7JS5Jw0D43Msa6Hdw9EMqN/cYSHejxN1DXtn/TyqmvDMwRXgwAIgAAIlHkCJRYCTODrr8ZQarMZtO37II WN4 iO5IW0NNvnwwksIlv69MDtPrMErpO8XaFnp9o45MpdN 4/fTNeaLa3oz45/auoTsuP0irpnSmZ7Z2o/pHptLqXcF6dNsHCz2n6e/TrqG j/ XTp2/jIbO g9NfaQq7Vr5G rYd6vvbwMyP6Q5f76CLigq6txPe2j56Jtp6NyvQtpbk 6gpd9t8J5jQMTXTO/RlLI21KWug fT1PRO1LC6KMHdWDjyr8F0261/pV0niZpcNoTmv/sk/eYqop1v3k/3dHuRPveqgpT6I2nJh7OpXZ1gmbEQAiIs8PL hjT19S9oRCd3NuAqEAABEACB8kMgKkJAt62PEV3TKIsWbBtFtQ7cTzdet4r2SecB6bLa97zSgdqnve8TAT jSvRwxnGaM EXPtosEpb2T/btdZc/qhDg616fmEz3eBPqOLO XcpC2rSrP3n9OOV7dtPodlfT7FyiX1BDSn/1CxrVJVhagecIPX1PXRr5Umgdqb/7gHJy2nv/uIUebvVHapS hcZ1rRb2KDi2YyDdeP1Cn7O/gGrQnxd9TZP7Bot5ZZSHus3y/7uZ98Cml37MLJbwF83QwIl//YFatltFyedH0iv5s6l5hHkGYYPADSAAAiAAAglDIGZCoC6l0bKjq m3NYl0QqFjxzdo08bgFPScZxMNbNKJlv3Xz6YG3UoLjm6mrt77xeeHU l0a/1JISsPqhA4 fkAurbFooDoGDWtkGaMCZYhlsL5L9fUm0MbvhzuPSYp Mnz/J36Nu5Cf9sb/FtVakEzP/w31XutDr1W4TN6emLVsDuQRcj466 mGR9a23fs1dAtgLos/mgKASE8uniFzjqf0MEHBEAABEDANAIxEwKyg3ZzEJDYy37SuxrAnytpCL2UP5daSbNUN WIrXBchi5uLjtSPoHvmc 3Uq/God0ur0yIby6uXZt VTeb1niPMw5/LYBIzL4PF9kntv3J2f6qiOEQyov5S6idxCBaQkAIr9X/rU Zr3xJj6aaNvRhLwiAAAiAABNIGCGgOjjd4UVOQkD93kkIcPhh3DM/UMYfQwcDhwgyO9WlSZuCf7/A6/7H/t8JyngwsoHz2p89dNe04L06 1QhcCE1pSfe Ywevil4X7SEgKiLzhUXXJFZiLtAAARAAATKIoGEEQJqMlwkQsAp 1/XQUMn/khPT1Zz9IlUp8z3luRkRTf26epUdyVESwiIchAWKIuPLdoMAiAAAtEjUK6FQDJFvuytS07kFYQHJ39FcyPIEUgkISBWTpbuiJxP9IYgSgIBEAABEIgngYQRAnJsn4HU9iYbvpC/mm4KI0dAbIf72/4g0nDO3Fc74qu376RWt79OXxfF9fl7q62PTp2YSKEBsfJw7lzxHAQnO/A9CIAACIBA SKQMELg0wVXUbPBnwfo6hL5nHIECjzHvbH9miGx/RaVsmjD6fEU7g/r8u6Bfk3G0enWZ2jTmn0hZwuI7YThnCCgJkM2pTH0asF08h4hEPiouwZilSz44RMX0fXjvid150b5GtqwBgRAAARAwA2BhBECZ87 hTrWeow lA4lemDoIVryVNCF//D9LLqr6aP07rGgaer2QfXX Xg5v/fwnfRcdsPA4UF8Ny/9vzG5B311 yvUTzlfX5wnsKfldzRr0hbtdsInP/iEBoZxLr8qYnS7Bg4 fw1d3vvjgHG60/5KmiMgzlKYm1uDJi77mh7r7WaY4BoQAAEQAIHySsBSCLyT6aFbJoaabZUs5zRTd/pe1LLZW fd3jrFT zy/v3MzR/R0FsL6NDOafSH26bSx9/9RGfOBNvVhB6hF45Pp18VnfDHdT1yTXuaG/SnVNF7UkCXB56izCd/R82815389j2a/8de9HHlDbRsQYsQgcAiYFH/K2jFf5bT2qKtgrrthFYH/tgNFPlAIV3 gnzGQawOFPr yHBq3 j/6NRP9xXbmlheBznsAgEQAAEQsCZQTAjwTPmr/UvpwVsfpPX7Qm9kh9p30ps0Y1xzqir9xK3uiOHL6C6av/cV6npFBTryrwfolpuX U7UE58G1J WH59HN0pH9Ppm4n oS NXBcWAuJ7rvu/JuZS0KI0W7ixukHz4zpnvltN9bfvQy3v0hv MLqK7732FFqy8OXAmANv9vy9epoz D9KSd76j x/9mubOqOETCWcLllOPhn1o3aHQ8m5ov4hWvdGP6lZ2P8Q fa0rde79Kn3hPWK4ofecgGc/nU93XHWOPt4wkP7QY5WPUaOLBnpt/CvdLB0xzDWc/uENGtnhDlr472B9fELhQ5n/pif XKfY7xPoWvXP2ZfSr722/fY36 n1t 4KEUHurcCVIAACIAAC5YVAiBCw gEhnbFidaByTluqlbZdy4P38Q8eX5dmTd1s b36Qzn8OwG Hyqa/hbt ewEnfUu7deqdT2NmreahnT9jIZecxv9/X NqNn1janF1XfSDTdcT22urkO1618U4tTO5n158dRxOf3eQrhzVIcpVLKaVhKv35uWzq1q5y4HqrI5J5 X72rmo0odXikOORZWN0S/xOg0P3o0PctsvrtqP jz5BIwakxORHh/I9e72nGzam7A LH2/s1GZ8DwIgAAIgUD4JWIYGyqe5sAoEQAAEQAAEQEAmACGA8QACIAACIAACBhOAEDC482E6CIAACIAACEAIYAyAAAiAAAiAgMEEIAQM7nyYDgIgAAIgAAIQAhgDIAACIAACIGAwAQgBgzsfpoMACIAACIAAhADGAAiAAAiAAAgYTABCwODOh kgAAIgAAIgACGAMQACIAACIAACBhOAEDC482E6CIAACIAACEAIYAyAAAiAAAiAgMEEIAQM7nyYDgIgAAIgAAIQAhgDIAACIAACIGAwAQgBgzsfpoMACIAACIAAhADGAAiAAAiAAAgYTABCwODOh kgAAIgAAIgACGAMQACIAACIAACBhOAEDC482E6CIAACIAACEAIYAyAAAiAAAiAgMEEIAQM7nyYDgIgAAIgAAIQAhgDIAACIAACIGAwAQgBgzsfpoMACIAACIAAhADGAAiAAAiAAAgYTABCwODOh kgAAIgAAIgACGAMQACIAACIAACBhOAEDC482E6CIAACIAACEAIYAyAAAiAAAiAgMEEIAQM7nyYDgIgAAIgAAIQAhgDIAACIAACIGAwAQgBgzsfpoMACIAACIAAhADGAAiAAAiAAAgYTABCwODOh kgAAIgAAIgACGAMQACIAACIAACBhOAEDC482E6CIAACIAACEAIYAyAAAiAAAiAgMEEIAQM7nyYDgIgAAIgAAIQAhgDIAACIAACIGAwgYQSAqe27KFeM/IC3VG9dR1aml7N9 8Cz0EalPo9HSv6Vv6uLPafao woUFqI5o7KLksmmTbZrlvK RVoREbLqdbPETbVuyizNWF1HZIc3r89mARy7M odVbK/j UKnGJdSu8TF69/1k6prdlPo3cY/n7IF9dN wH4lHVVL BWHfr6tJtJm/E7ZcuOwQ/dCnnq1N7luNK0EABECg9AgklBDwO/wTlP7QEfrosNdLeD qY8xdtpd2tG8UljMoPZzh1yScSrSclFULcpcGHVX4rYzOHUIMOAkBweTa4VcQ5eyjj7 oSs1vPEk7PghfCHDLhRg4HwUhwG3L tvPAoJCCLpvXIib6FBEKSAAAiAQXQIJKQSeXHyGfth2MiAG5NlieRUCsnOMbhf7HWGfB39GfyyahUe7fLflCYecLzlN3b1iNUBdJXBbj3qdcNbHSygEhEjd/VMNylpUixoVVcTlP3RHId37mn VAx8QAAEQKEsEElIIzF5YSENu/S6wpCs7SQiB8IaXbsYaXgnRu9qNEJBXhBJVCPBqlRqaWpG5n pOaAghEL3hgpJAAARKiUDCCoFH 19CclyZ48Q8C/tGCQ2oeQWyaJC/4xd3x SDvrizWIZvvs0fn aPGoKQ48CxzEcQ9TitCOhyCmRHKbdX2PPU4K9D8ir47zpb5Hvrd61Fl/7zK99qjGjToanBeL3qnOV7deENOdaf8ruLaN/a70isCFRaGcr/qcFnQsJCwo52X38eyBewslm1S25XPW 9ed56S7oiwO1Rx5vduOHvdDZxOTIruW9jHSIqpfcKqgEBEChDBBJaCDBH1SEPaXwikCOgznaFw5KdguyI2Il0 jrU UxNOehLUNTFrf0vcr8z/UWMkvjcCgF5uXxkJX9SpWjzzUn RErRRi5z Y9X0pMdz9HOL/9Hk54MtU8dn/IsXDiiC14Mdf6CmxBkvCyuJvpxG9dICX3ie EshQ3BdgfzQcQ1uhUB2VEKISCXrfaRcNZiHEQ7D0MVXaFOPdQmFgLTJp lnpPq0KVSMmzQXn/fiRwDFkdTV1QOJFOWoXcJmgoCIFBGCSS8EGCusjOvcmll6ji2gTZZULygdUJAdQrCoYmXs qc/vVlRV9CWN m/he7GheOVn 7FQJyfeoS 81JxR2quF6XoGcnBFSnbcXtiqJdHPIsW a/OON0YDVCOG837ZaFgOoseccIlzXhDr 9uj7KXFyRVhYlm6r3R2NFQLBTk1qFGBDjhVdU5NUC XpZTKmiRfw7WmGRaI1TlAMCIFB CZQJIeC0dKq lEsmBEK3KYqud1q6j3SIhCsEdFvXOEFNN6vnbXaxEgJ1i7blyZn4om3s6DIW59H01FMhy/HREwLWfTTsjcq0pUgICGcavWTBg/ToxMo0e4p/Syt/5LHJ425xRmEgvCELAbnf7EI6otzyuo000ucE94EACMSOQJkQAmy 1RYweTlaxPyjJQRKY1ZmJwTYuavLyuwgZnY64kuk1GXfq862zT9Cwwi6rHbdLFyswiTmikBQCKh9ZLeiUNIVAXb6g /6ka6fHXqWgWBe2UIIqGJBnI3B41oWT/JOhNg98igZBEAABEIJJKAQOEhD 19Ajy4Mbs8STebZbe9phYE93LLTk2eCJREC7CiFExRLuFd4HXLGwFN003MNop4Vbhe/5nZsPls/ZJYp5znIOQLy9jUuU8SZ23/pP1CHRcPAeefp/U11aKpyYFEkQsBNjoCVmHCbI2AVGuCDh z6SCQhquGfkibi6XIVhDMXZwvoQgNqboRvjP3lUzrXI4V6VQweeCREDY/z8Z/WL5cHS EFDAIgkHgEEkoIyBnZVi9tefugGjLo0KMCvZdz1keZX6oiqU5gF1nr4uxCkU0uTiuUY7dyXkJJHYiu261OFlSvVWP2/L3cbv9y9GkaOeU8/fDPM4GTF4PL4sH8Adk uR4181/myNep3KySMVVOasjmkjaV6JS3jcyf25J2ywla qJ/1wZ/xAFC4jAp/hvbL 8akOuw6yP5u6reepOL2JQkxMN9JkTqB9LJh7pEU2FT8/uq0p6V3/tslj/yPfLph3xNLHepJN4rCC0CARCIN4GEEgLxhoH6QQAEQAAEQMA0AgklBFLv3pnQ/Ne92jyq7Ut0e6NqbAIVFmk/lnZ/RdrOBEKNpoAACJQBAhACYXRStF/Mpe1YwjC1XF8aaT Wdn9F2s5y3XkwDgRAIOoEEkoIRN06FAgCIAACIAACIGBLAEIAAwQEQAAEQAAEDCYAIWBw58N0EAABEAABEIAQwBgAARAAARAAAYMJQAgY3PkwHQRAAARAAAQgBDAGQAAEQAAEQMBgAhACBnc TAcBEAABEAABCAGMARAAARAAARAwmACEgMGdD9NBAARAAARAAEIAYwAEQAAEQAAEDCYAIWBw58N0EAABEAABEIAQwBgAARAAARAAAYMJQAgY3PkwHQRAAARAAAQgBDAGQAAEQAAEQMBgApZCoEfPHgZjgekgEF8CNWvWpGfmPhPfRqB2EAABIwhYCoEhQ4dQjRo1jYAAI0EgEQlMmTw5EZuFNoEACJQzAggNlLMOhTkgAAIgAAIgEA4BCIFwaOFaEAABEAABEChnBCAEylmHwhwQAAEQAAEQCIcAhEA4tHAtCIAACIAACJQzAhAC5axDYQ4IgAAIgAAIhEMAQiAcWrgWBEAABEAABMoZAQiBctahMAcEQAAEQAAEwiEAIRAOLVwLAiAAAiAAAuWMAIRAOetQmAMCIAACIAAC4RCAEAiHFq4FARAAARAAgXJGAEKgnHUozAEBEAABEACBcAhACIRDC9eCAAiAAAiAQDkjACFQzjoU5oAACIAACIBAOAQgBMKhhWtBAARAAARAoJwRgBAoZx0Kc0AABEAABEAgHAIQAuHQwrUgAAIgAAIgUM4IOAoBT5LH1uTCgsJyhgTmgAAIgAAIgIA5BGyFAIuAk/ ebUvj4laPEMSAOQMGloIACIAACJQvApZCwI0IEChYDOg ZUEgnNqyh7LPNKHHb49ux578fABd22IR7TtHVJma0cwPdtGD14XWMSfNQyNz9N 7uT/Pk013VhlDeSkraEtuD1cGnPdspaEt2tO7OybQ oJMaqTcdTSnLdVK207jZxVS1khXRZKdHaKTv8ZfXot5tWLUyxLditXaLeFNLbIiqRWXZos6oYK1EOX6/73h0FXAUCIAACZZOArRCYMaQ5DRo80Nayvz63wPKasrBasCJzP9Wd0JBusY AhNW77Mju8Ryn7CJHy47msZxQMbBpkoeGZ/gd2CVe0dAm5UMaXSQW3Nzv5Nx0DRYO9q3T50jnPLlNnTL8d7oVAnZ2CBGwM9nvfMW/v/21tRhwY5e4puI5ewHAdgib26Xn YQN98WaA0ExwO1/u5pf9Ihy67QqLhbCGgC4GARAAATKEAHHFQF29HYfO6HA945 ZmephQ5yl 2lHe0bUf8m7nqgwHOQHp1YmWZPqebuBpdXvTl DCVlPREQF8IZ1Uj7xDcb5n939jxHadIqATuk9A1 B R0v9wM1bG5aaLsvNUVAdVx2pXnZIeuLNlOu7Kt7BLOuk1v55UFLl tT25zv/bZlDXgTpq84KpAU/j6Phnd6Pn8tVEVh276BdeAAAiAQDwIOAqBSBslBMSL2y k3NzcmIuBswf2Ue Hz1Pn7KauhUCswgIqM3UmzMvvrdPqhjgb3d9EOXYz6XgKASc7bkgqHrrg9h69wTnsoLPLKazhxJ2/d1qVsOuHSJ8F3AcCIAACiUwgZkKAjWYxYCUECjwnKP2hI/RFzbo097bj1GtGno9TW284YnTKPrpv2I/Ef2mQ2ojmDkoOMGTnLa6tkFeFRmy4nCqt3EWZq4O7FyrVuISyFtWi4ytC/66WtWrJIWrTt16xOHm0O0ydOetm5DzTlcMDcht0M2/xfTyFgBs7RM4B5wbMHzuDuve nTa7yGfQ2SVWA9qOGE25c2b48i/UEAffNy3HP6MXQkSEBdwwc7tiEe0xgvJAAARAIF4EYiYE7FYEhAj46LA/MF 9dR1aml6Nlmd9Qqu3ViDhyC/1Ov37//Jzn7PnGD6LgKGbaviu5c82r6Of9VZ1n9Pna3tPK6SuRSsC6goBXzt1ReVAWRwWyP5rTfrTwKDIiFUnsDPsPn1UIEnNjQOV26LeL3 X6EKA2ypyD5yS pzs4nJ n9GMWnbsRss2ZlH9omTJI6fHaBMfrcIcVsx4tWBY877UesGnxRI7YzU2UC4IgAAIxJtAzIQAG Z2RUDn2Dl2zY5fOPe Tf0rCEI8CHBJ Rf4nH/a/0KFgAxWCAyxgsCi4vR7B2h17QauwwiRdhQ7l GNplPanmDMWScE2Nk3TjtdbHeB7n4nh nU1mjlCLixQyQ Pr77CN3bcjG5SfDj9uucta4 IQ50uzJ0QkBNYFQF1/DXljnuanDii 9BAARAoCwRiJkQcMoRkEMD4QiBCt1 qd3qJ4sGkSzIqwAcMuBww8hKwdWFm5NO0LTJZ6nnpDoxDwvM6d6AkkcdCJlhOsXW5R0MuvudhICc/c/Xqlv2whUC6hZAsR2y22H7XIcbk/xbFav39 cE2Dlh9aFxKwTsQiq6fACrHAEux23YItoPuBVfdbtptOtFeSAAAiDABGImBGK1InD8V41DcgZEN6pCgP thhXEv9t/uY mbKxDU6Xcg1gMB3lrmly LuZv5fjE1jar9sUzNOBkh85J8986ptSmVZozDJwEjq48p Q NeavK0PdrhmLsYAyQQAEQCBRCcRMCER7RYBn SJRkGf44gCg3KWH6Ic 9Yidu9g1cOH7h6jJFT/SlCeCOQMcHsh572JfjsCFy8PbZhhJ57EDWnAodIvbU91SqcXadb58B9lB6ZyT0/3cpnBm2KqTnZej34MvEvJ6TnfO7Ocy7ezQHQzkJhnPzi4WPqLtDYoOR7I7l0AVK6pw4u 7eN6j8fkvBbYLMoOx00fTfIeDjyIZF7gHBEAABBKNQMyEgN2KgC5Z8OGmXwUy/zmWf//4s7TkSW9auPcj8gBYDIjlfgFS7ATg5L9Bqd/TMe8XLBQm3BH8N197RZtK9MU/z5Cn4Gd0WbOqNG5G7ZiFBeST6uQOV0 tszqRz8398sE7XEctct77Lh8oxPeoJx6qIQW3p zZnSyo1ulUppNdTicVyrsGRIjF6pAitS7RV1YnQSbaw4v2gAAIgEA0CMRMCDitCESj8SgDBEAABEAABECgZARcCQFxjHAk/y2tA4VKhgF3gwAIgAAIgICZBBx/fZB/byDSD4sA/uhOFky9e2ekxcbkvnWvRm5nTBqEQkEABEAABECgFAjYCgGun3 FsG3bthE3hUUA379t67aIy8CNIAACIAACIAACsSHgKASEGIi0eoiASMnhPhAAARAAARCIPQFXQiD2zUANIAACIAACIAAC8SAAIRAP6qgTBEAABEAABBKEAIRAgnQEmgECIAACIAAC8SAAIRAP6qgTBEAABEAABBKEAIRAgnQEmgECIAACIAAC8SAAIRAP6qgTBEAABEAABBKEAIRAgnQEmgECIAACIAAC8SAAIRAP6qgTBEAABEAABBKEgKMQ4JMF7T6FBYUJYgqaAQIgAAIgAAIgEC4Bx98aOPnv2bZlXtzqEYIYCBc7rgcBEAABEACBxCDg6tcHnZrKYkD3SRSBcGrLHrr/Lz nERsuJ/Eb9U42ufm wHOQHp1YmWZPqVbscvm37q1 335OmodG5hDpvndzf54nm 6sMobyUlbQltwebppM5z1baWiL9vTujgm0viCTGil3Hc1pS7XSttP4WYWUNdJVkWRnh6hv/g5/WT367aZVC1NsC3Zrl6g3hfS2iEpklh3arCrGSpTD1 u d0cBV4EACIBA2SRgKwT4lwcHDR5oa5n4aWLdReV9tYAFRvaZJvT47aHWsyO7x3OcsoscLTuax3Ka0cwPdtGD1/mv3TTJQ8Mz/A7sks8HUJuUD2l00fdu7ndybrr EA72rdPnSOc8uU2dMvx3uhUCdnYIEbAz2e98xb //bW1GHBjl7im4jl7AcB2CJvbpef5hA33xZoDQTHA7X 7ml/0iHLrtCouFsrm441WgwAIgIAzAccVAXb0dh87ocD3jn5mZ0ShgxWZ 6nuhIZRncE74wjvCqs2vjl DCVlPRFou3BGNdI 8c2G d dPc9RmiIM0jf4HZDT/XIrVcfmxgLZeasrAqrjtCvPyQ5dWVy3sNOubK8WnJoAACAASURBVCu7hLNu09t5ZUEILrk uc392mdT1oA7afKCqwJN4fb1yehGz evTeix56afcQ0IgAAIuCHgKATcFKK7RgiIF7dfSPxTxOGECWK1lB pLbr77MIC6vXqTJiX31un1Q1xNrq/iXLsZtLxFAJOdtyQVDx0we09eoNz2EFnl1NYw4k7f0KmHXD9EcPygLBEAABBKFQMyEABvIYsBOCGxbsYsyVxdS9dZ1aEjjE7SjfSO64MVPaPXWCgE /N3S9Gq0PCv07229YQuxJH/2wD66b9iPlKdQbZDaiOYOSiauZ9Zb1SlrUS1fTJz/PXVFZRr6BtHfUk/RMe/fRD2iCLU /nuFvCqBPIPT7x2g1bUbUP8mzl2pzpx1M3Ke6crhAblU3cxbfB9PIeDGDpFzwLkB88fOoO69b6fNLvIZdHaJ1YC2I0ZT7pwZtO8cFQtx8H3TcvwzeiFERFjADTO3KxbOvY4rQAAEQKBsEIiZEHBaEWDnPWBKJUr3OudLvbH23tMKqWt2U59jFY5aJPepKwTspNf/91KfY7/Cm7A3KPV7 kWR0 dre83IIyEUhNioVOMS3/XHi8SH7Njb/MO6/puTTlD6Q0do9081AkKC71215BC16VuvWLKdrtvZGXafPiqQpObGgcrlqPfL3yW6EOC2itwDp6Q J7u4nN9nNKOWHbvRso1ZVL8oWfLI6THaxEerMIcVM14tGNa8L7Ve8Gkgl6NsPMZoJQiAAAhETiBmQoCbZLciIGbxraWZvTBDFQLi7wUev1P 6LCHhGOv6xUUvR8 T52LRAQv2cvCgO 1WhEQQoPbIpfBQmPz2fq lQhxP68giOu5juy/1qQ/DUx2JM/OZXij6ZS2Jxhz1gkBdvaN006HJBRy4br7nRymU6OilSPgxg6R Pj47iN0b8vF5CbBj9uvc9a6 oQ4kBMxhf06IaAmMKqCa/hryxx3NTjxxfcgAAIgUJYIxEwIOK0IMCR5 V1emtcJAb52zfvJvlWD5ttCl/plx6069UiEgJMwyF221xfGcBMWmNO9ASWPOhAyw3SKrctbHHX3OwkBOfufr1W37IUrBNQtgGK7Y7fD9rkONyb5typW7 /PCbBzwupD41YI2IVUdPkAVjkCXI7bsEW0H3ArvmKHSbTrQ3kgAAIgIBOImRDgSpxyBERD5FwBnoWrQkA3o5dj/mqOgJw/EIkQUEWKWH3g/AJelZg2 Sz1nFTHMSwgb02Toeti/laOT2xtsxq28QwNONmhc9L8t44ptWmV5gwDJ4GjK88puU N evKULdr4hUBAiAAAiYRiJkQcFoRYOc9ZGE1Wigtvz/7eW3fcrzICRj2RmX6eGEhdah41Jfcx0vzasyecwQeuqOQ7n3N rAgnbCQl/rVFQC fvmPV/oSDdUPXztlYx2aqvlOvpYd0IJDoVvcnuqWSi3WrvNtS5MdlM45Od3PdYUzw1ad7Lwc/R58kZDXc7pzZj XaWeH7mAgN8l4dnax8BFtb1B0OJLduQSqWFGFE3/fxfMejc9/KbBdkBmMnT6a5jscfGTSiwK2ggAIlF8CMRMCTisC7FBHZp2jw1 d99GVM/LFDP98/gW UECvisFdAUnev13evoD25 b77mGxsKUob0DuJlFepZX nQmijlt7naKNa/xX8jUD552nxcODOw54NWFkJX/CofrhXQh9fn7YMSwgn1Qnl6GeWmd1Ip bWDd7iOWuS8910 UIjvUU80VEMKbk/ZsztZUK3TqUwnu5xOKpR3DYgQi9UhRWpdoq sToIsv68BWAYCIGAygZgJAacVgWhBt9rPH05Cn9oWqxyA3KWH6Ic 9XDQTLQ6D WAAAiAAAjEnYArISCOEY7kv5EcKBQOFTXDX9wb6cmEumRDLtNtSCCctuNaEAABEAABEIg3AcdfH TfG4j0wyKAP7qTBVPv3hlpsYH71r3a3Ju8598uyIcCyR RMBhuPVymSF6Uy5MTBtUy R58QAAEQAAEQKAsErAVAmyQJ8lDbdu2jdg2FgF8/7at2yIuAzeCAAiAAAiAAAjEhoCjEBBiINLqIQIiJYf7QAAEQAAEQCD2BFwJgdg3AzWAAAiAAAiAAAjEgwCEQDyoo04QAAEQAAEQSBACEAIJ0hFoBgiAAAiAAAjEgwCEQDyoo04QAAEQAAEQSBACEAIJ0hFoBgiAAAiAAAjEgwCEQDyoo04QAAEQAAEQSBACEAIJ0hFoBgiAAAiAAAjEgwCEQDyoo04QAAEQAAEQSBACjkKATxa0 xQW H/ZDx8QAAEQAAEQAIGyR8DxtwZO/nu2rVUXt3qEIAbKXsejxSAAAiAAAiDABFz9 qATKhYDuk9JBEKB5wSlP3SEvqhZl5amV3NqQql z22bNvks9ZxUhxpZ1Cz/1r3V79vPSfPQyBwi3fdu7s/zZNOdVcZQXsoK2pLbwxWD856tNLRFe3p3xwRaX5BZrP1Hc9pSrbTtNH5WIWWNdFUk2dkh6pu/w19Wj367adXCFNuC3dol6k0hvS2iEpllhzarirES5fD1uu/dUcBVIAACIFA2CdgKAf7lwUGDB9paJn6aWHdRpKsFQgR8dNhD1VvXSTgh4PSTxOzI7vEcp wiR8uO5rGcZjTzg1304HV UpsmeWh4ht BXfL5AGqT8iGNLvrezf1Ozk3XH8LBvnX6HOmcJ7epU4b/TrdCwM4OIQJ2Jvudr/j3t7 2FgNu7BLXVDxnLwDYDmFzu/Q8n7DhvlhzICgGuP1vV/OLHlFunVbFxULZfLzRahAAARBwJuC4IsCO3u5jJxT43tHP7IwodFAaKwL8E8aPTqxMs6eEt KQu2wv7WjfiPo30ZN5c/wYSsp6gm4pSq8QzqhG2ie 2TD/u7PnOUpThEH6Br8DcrpfrlV1bM5dHipC1BUN1XHaledkh64sdrzCTruyrewSzrpNb eVBSG45PrkNvdrn01ZA 6kyQuuCjSF29cnoxs9n7820H9umOIaEAABECirBByFQKSGCQHx4vYLiX KONwwQWkIgeVZn9Dms/XDWnFwExZQmakzYV5 b51WN8TZ6P4myrGbScdTCDjZcUNS8dAFt/foDc5hB51dTmENJ 78vdOqhF0/RPos4D4QAAEQSGQCMRMCbDSLAZ0Q0C39b1uxizJXF1KlGpdQ1qJadIWUI9Ax SCt3lrBx7GtN1wx4Q5//oAcOrC7f 5tx6nXjDzp/oM0KPV7Oib1TJM7fkF7Xv RkvIvoK7ZTalv0 A1XOfjt/sv5rDAok vpIeL/u2mc9WZs7ycLmbkPNOVwwNyubqZt/g nkLAjR0i54BzA aPnUHde99Om13kM jsEqsBbUeMptw5M2jfOSoW4uD7puX4Z/RCiIiwgBtmblcs3PQ7rgEBEACBskAgZkLAaUVAN NnZz7rreohQoCdvXDEPINf835ykaMunkwo7s9cXJFWFgkF7gSRZ8D3r//vpcWEhkhGPLVlD/WeVugrn5f9OXTAgqGhJARylx6iH/rUC2vZmJ1h9 mjAklqbhyoPHjUXvEl0IcFtF7oFTUp TXVzO7zOaUcuO3WjZxiyqX5QseeT0GG3io1WYw4oZrxYMa96XWi/4NJDLURYeYrQRBEAABEpCIGZCgBtltSLA37kVAvKuAeGYf5HaiJ4afKbYrgKdkJDvd/reSQhwm2cvLKRH 1/imjk7l GNplPanmDMWScE2Nk3TjsdklDIlejud3KYTo3T1S/uCSdHwI0dIvHx8d1H6N6Wi8lNgh 3ReesdfUJcSAnYtrZoiYwqoJr GvLHHc1OPHF9yAAAiBQlgjETAhEa0UgVAj4VwGO/6pxXIQAC4XsM00CYQI3HT2newNKHnUgZIbpFFsXSYY h6i530kIyNn/fK26ZS9cIaBuARTbHbsdts91uDHJv1Wxen9/ToCdE1ZZuhUCdiEVXT6AVY4Al M2bOGm38O5xoqv2GESTlm4FgRAAATCJRAzIcANidWKAC/VizyBcGb8JV0RWJG5n pOaOg6LCBvTZM7Rhfzt3J8YmubVcfGMzTgZIfOSfPfOqbUplWaMwycBI6uPKfkPjXmrytD3a4Z7kOE60EABECgLBOImRBwWhFgaKEx 2ByHicMijj/7p9q GL6nFQnX6/4qieD4nAMr3WwkFcT/vGpg/4FtfAmD/lH1037AfqXVRToBIQOS2XjOyJp169wLXWw3ZAS04FLrF7aluqdRi7TqfkJAdlM45Od3PbQpnhq062Xk5 j34IiGv53TnzH4u084O3cFAbpLx7Oxi4SPa3qDocCS7cwlUsaIKJ/6 i c9Gp//UkDgMYOx00fTfIeDj8ryg4 2gwAIgIAgEDMh4LQiwN9zBj47Xs7nr5BXha7vdYo ese/a4Adtby7gK9XDxeyul XLPhw0698uxL4w3WN2HA5VVoZulNBiAOxQ6He7y6ivLXf ZIFR1ZyHxaQT6qTh5p6ap3ViXxu7pcP3uE6apHz3nf5QCG Rz3RUA0puD1lz 5kQbVOpzKd7HI6qVDeNSBCLFaHFKl1ib6yOgkSrw0QAAEQKI8EYiYE3KwIlEegsAkEQAAEQAAEyhIBV0JAHCMcyX8jPVCoLEFEW0EABEAABECgrBJw/PVB/r2BSD8sAvijO1kw9e6dkRabMPetezVyNgljBBoCAiAAAiBgNAFbIcBkPEneA33ato0YEosAvn/b1m0Rl4EbQQAEQAAEQAAEYkPAUQgIMRBp9RABkZLDfSAAAiAAAiAQewKuhEDsm4EaQAAEQAAEQAAE4kEAQiAe1FEnCIAACIAACCQIAQiBBOkINAMEQAAEQAAE4kEAQiAe1FEnCIAACIAACCQIAQiBBOkINAMEQAAEQAAE4kEAQiAe1FEnCIAACIAACCQIAQiBBOkINAMEQAAEQAAE4kEAQiAe1FEnCIAACIAACCQIAQiBBOkINAMEQAAEQAAE4kEAQiAe1FEnCIAACIAACCQIAQiBBOkINAMEQAAEQAAE4kEAQiAe1FEnCIAACIAACCQIAUsh0KNnjwRpIpoBAuYRqFmzJj0z9xnzDIfFIAACpU7AUggMGTqEatSoWeoNQoUgAAJ AlMmTwYKEAABEIg5AYQGYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hJwLQSO5rSlOQdzKWtk7I05 fkAurbFItp3jmj8rMKI68zzZNM9nuOUXZBJl0hl1qJu9Hz WrrF484WLqeL5z0an/ S5T1ym63Kn5PmoZE5/jrDsYvLHvl0F0p 9/c0f0ewzR3arKItuT18f D qZW23ff/XP/ACS9T5l IUmgCrffa38idqTG7ihn2aVuHXtjmb6/V57xnKw1t0T5gJ3Oa/Eg2ZQ24kyYvuCpm7UPBwTGUKGOmvPTJpkke6pSROM izJWfyzurjKG3TntfttKnMjWjmR/sogevK51eEIy4Nt34k9 v8nuvdFpX/mtxJQR4sHT2PEdppTgw3Dhfp 7Z/Hgn2nvXRupZfQB1TKlNq4ocIjvkeTnuHKR4UPJSVgScrlovD1K78oVze3eHv04WJe1TTtCzLsQIPyDDM4Jt5X/3ydALGW5H996302ZJHAx/bRmtWpjihKpUvhf9Yfdy4b5ZcyAocIR4Ckc4lYox5bQSHl8LDu1OmDETL8wsrBunnY6aM Tyuk8fZfkOiZedXK94x9VI yTQ7/zcTcsJb8IUqQ3M5jdpnQITFq77g6rBMcjvtTYpH9Jor/8Z0N4/UajeP/IJYqTtLM/3OQoB4cRe2VE6g0LALumDozpFuRP5OzeOmG0f1rwvfdnkDFWuvtH1y1Etn21pnVY3sAohmDoNZt1LWXWUsl3HVo gtZfPCah4vvboDbF7YMJdJWIuY6ePpvkWwkQnOJnV8EbTKW2P xWcRHxg2Y5RnV6lYW9kxX11xm41hsd76wWfRmUmGO74SMR i1abYv0slqSduucumkLIaRyo7zT53S/eld/ OigM L2YviE4WSiJ7bjXT8BRCPAsbkNBIT0/tXJYy klBVzSB epbqnUYu067VK OoPXtVWIgKuXv0C77v9DWC9HufwGRUvdO5ODA1co8HbpeZZhD50QcrrvzfFjKCnrCZ/N0VhRsetDt2JKLkMO1ehCFeKhl1nx/fPGjaHbpj2RsA7UzVhXZzlu7inta5z6J5z2RDI wim/LF0b62expCzUiQqXZ7fyGE59bsaBWhf/1q/gmMTpDYTYbCaRuuDRKwFQLcCby0/FTnPiFLNyIezXGkrI ep50PXOOL6epiO2Jpl PW93rj1tvfKO4QRXxKLP8KJ8wzk37t/TGs3NONQ5bpdLFkkb/gNPOUB5rVYBBCZEzn0GV/N4NHLl 37CYvdemWya2 1z2woj3MY LwLyhrzr2 Pwkh0b1BT19eghzzE23adfqugLgT4mVlYReaXRSjF7E4Nca5Xsp1EOVeucEfB 3RL6jcVTHn5qUgxpZdHFDOteD6Vi46Gcgr4H8vX/S6b8x82foOKti2LiTXRCemdPkdn/Tw53NwO97efrmvfBHascq30I31dSveCOS7cL/Y2SW347ZRo6lg5vqQcJycByKeNdEXunYKESrySuS EeNGtJnLm7dqIz02I3T52o51OONDN87VvBY1b0fHc83Ymb5cGDHuxPuB3yFy EiNfYvv5HcXx8DV zkfRcTMVV52cWy7vnOzumnVXu4nq 9EncfO eP54hlU 0XX7/J7TDcjZ8byfer7VnyntqHbYX uEvO 7P1gTpRdzoEcOv3t7/5Cxy8OfYfIYVyryYKb9zKusSZgKQTk5C41Ts3F8QBod/f7lP95ki92Ix4oMctVHaAYMD2nB5WeGDDswGWnIZzSssIaNLIoSY9fzGKZWy1LXSpyWg2Q4 g6NHJb3DzEchlqSMJqaUuO 6ttsMphsFPCXO/iDQvpkRH 0uTYevoj/rgaz7Tf3H7El/jYf9fFNPPqOoG8CSH6RD6BYMAPM8fr5o dUSwPQvSHCGFc/32zQB/plvTdCAExtjhZtOK50DwOdUwViy12b0D5kx j11tuoJ91W0tVqgVFgrzKINsqz0ZuTAqNP/J3r9XbQWfn3OMLD31/eKY2xus01t2sQKmzInUMyP ur Ts6NopBEib3v6Xqiou1dwX9ZlyZF0UdnIzPqyeMRGDviEpNBnXLc9ndx hB5p968u1kd8PwtnLzl8OzYn sLpfnoiwgNHl Mg5QW76zi5Ep7ZXff/I70l1MiBsedIr4p59fRkNrNfMl PBzyI/t LfVnlCumRB1WmLsWE3ljgpe5S3DQ8tu4zq/n1vQMC6Wdllm 7f9hvKn5dNci6WbhKl xscfMkJWAoBeSagm8mo4kCeaQnHI8d15DiUKhpUM7jsp799nuq9ttoXG5ZfFPz/rNhFYovqaFWHJpftZulTjcu7GciiDqvy1Ze43H7VdquBXtKwgCoi5KVqNWdBLGX2fOEg7T2y3bdEJ3PRxRR1eRFyAhDbqROUVkNYvHyEGNCFWGSbuE13N3zXV9zYfaH5BGq9IoRy9UuhCWGys SkJM5NONDiI7p77JeWMXOd0FP5OMU0rZZmRRxUdTTy9Sxe1HZatYnHHQt1WRiKXSeycBOCSBZPKmsWk GMD7mfnVa2WLRavTvYMYv3w5Wf/ceXc8HCSOzqEe8HOeymiiC7 zmspgo3u3Hr1HdOYQG759pq9UokzgkWw/9fF2p17H7fjhzup80/daEWv13n62ennA 7vuA cxpLYvn riWX0cVH7w8kKvO9uveEbtIjkoNVMar mNZu5Cyd1n SlBKwTUpXM1vqkqZtFBQnWfnxya6S6 F45hn5IJL MUZR 6sgl1 fM63wtYnpXLL8Vr9vi3GdZp5Q832CVkuUk6U5e/5HY5Za3bla qbrvtWXZhAassZquwgPySl1 u6gOqvgz437 c8B21qprhe7DV/lZn4sLJC8ele3mIVQp5R4DqHNTtqdzXv8/wL3vykqOwXwjJI6fHBDKN7V4Qsn3s/DncJcIJwtmJZV/Rz7qXkO6x1zkJmY8QMFaJobqXvSzMxFK1EL78LD6WE9zaZfWylGfA3G55XDFL9Xv5GZNZWrEOd3wIdlZjQ3zvhic7t7fOE/1piT pUX0/qKttqnCyu1 MZbFzIlxHrYpqpxVFO5FhxUL0nRBsIpFbiCAxq3azEuUUb9cJBfUdZbWCqXtPqM 8upNCbo/uXWhVV/lxyfGxpJgQYPhyZrfuwVUHmHyNeMGqil6eBTstcbPiTZ3/Is0e1NxHRZ6VyysV6n59Hni6sw50wsUNbjcPklDNTspbvIydditYKXQ75a4TbvJSpM7RC1Hmm02lzKOCKukBNa8 bCoHnTCUt/RwgumQF78MvKjF7EDMSHVnUejyNuR2s7jkHAT 6OKNdis3opxFhTfT0qKzDFRxpsbu1ZUh3Xixmy0Jx 0UDrGaUYotokLs8pka/NHFrdXtfjoHIvcp5xXIgkwXanNiLcdtncaHzM7OsbrlyeJfhBh17wfZNjWmrBNO8thR3xVWwpzrdeo7Xl0Qz8q4YWfpmtatiw0ju3eh p3OFvl9ojpepzHsZpndaSzJqzHquSzqe0I1XtcW/qs NWnLt5t OaUAIhQkCn4HQPrqxy1fiZmAEJISA6jxNaxiwZR9c07UN7nwzdxy8vnaoKWgyGSbuq0VdvLKJfnghdbRAP6ghv0uLecauLbc/SxfvENi6n2ZraFlXt60SA1aqEW1FhpaLVl4DVDEpdirR68XH8kEUbLysn3/syJV9SSLXeSaWUVybQWmULGT/Qb9Z nngpdvDGS2m490yJrhJv VwEnnFzvO/nMyvS494Y7sInxvi2CzqFBbgOed yaq/60pXHJc a7Q58EgzOnAtugdU5HdHGl70Jk9kuttGpZejG s 9SZS8UsJJbjqRqtolhC4Lk0Fe5/GHPid8oTB5qVs4CE5i1AlQXZnyKoI66 pw2zdUL8lDfTf4n7Fe9UJXDNSwn1qn3fj448a7fcmnYkVEdT7yM6WGFHU8f 1dzZBnkeL9MOqFQ74w1i3fBt8P4vmWtz5bvV/E/ZwczM5V/rcsPOTVNHVlRe27Xn2a vqnyQuP0pFBF9EfP xBvBoqb31TRbf8LpSfGTe26AQN15074CLtQV5qyEnnHJ3GktWKh AkvyfUJFu1bFV0ye9ucX6AuqMIDj06BHxCQF0SF8ujYrlUVCVmTfKs3GqWImYUvAy 1OsQ7m25OJD8xSpSPs3KLtOcBwsny4jldDUTWvydHzCx5US0V7xIxGxK/F3enWB3OIU6y1SFgFP58qzT7WltdoJBF7rQZaELZmyv7pRD0X/qrg/mou6SEHWu3OFfjubDmfjFKDKVeWlW5sDtEZndwmY1uU0dusyJTx1clnskZFyotlmtBjktv1oxVftPzoSWk8HsHjX5GdGNdTmrX4RqdDNkeeeMyLZWM93V8Ws3VmRW6tiT7ebvcrxJucO8YkMOtVixtloNtBofugNg5PGpru644amudvH7QYwV9RnRjSG7 0Xb5PvkNsnPk7qqJGfKi2eJnxVZgKr5ImoZdpn6drZYTQDkusX4Uet0OkXQbixZrcTJIs7uhEKZra4d6rtF9wxFxxWaXYrjOQK6l7bTcbtmIy2Z9VYrCiUrNb53z/Fm8yePOhCVQ2riawlqBwEQAIHyRyBsIeA0 yp/iErfIvWEwNJvQfRq1MX o1c6SgIBEAABECgpAddCwGnJraQNwf1BAuougLLIxik7vCzahDaDAAiAQHkk4FoIlEfjYRMIgAAIgAAImE4AQsD0EQD7QQAEQAAEjCYAIWB098N4EAABEAAB0wlACJg AmA/CIAACICA0QQgBIzufhgPAiAAAiBgOgEIAdNHAOwHARAAARAwmgCEgNHdD NBAARAAARMJwAhYPoIgP0gAAIgAAJGE4AQMLr7YTwIgAAIgIDpBCAETB8BsB8EQAAEQMBoAhACRnc/jAcBEAABEDCdAISA6SMA9oMACIAACBhNAELA6O6H8SAAAiAAAqYTgBAwfQTAfhAAARAAAaMJQAgY3f0wHgRAAARAwHQCEAKmjwDYDwIgAAIgYDQBCAGjux/GgwAIgAAImE4AQsD0EQD7QQAEQAAEjCYAIWB098N4EAABEAAB0wlACJg AmA/CIAACICA0QQgBIzufhgPAiAAAiBgOgEIAdNHAOwHARAAARAwmgCEgNHdD NBAARAAARMJwAhYPoIgP0gAAIgAAJGE4AQMLr7YTwIgAAIgIDpBCAETB8BsB8EQAAEQMBoAhACRnc/jAcBEAABEDCdAISA6SMA9oMACIAACBhNAELA6O6H8SAAAiAAAqYTgBAwfQTAfhAAARAAAaMJQAgY3f0wHgRAAARAwHQCEAKmjwDYDwIgAAIgYDQBCAGjux/GgwAIgAAImE4AQsD0EQD7QQAEQAAEjCYAIWB098N4EAABEAAB0wlACJg AmA/CIAACICA0QQgBIzufhgPAiAAAiBgOgEIAdNHAOwHARAAARAwmgCEgNHdD NBAARAAARMJwAhYPoIgP0gAAIgAAJGE4AQMLr7YTwIgAAIgIDpBCAETB8BsB8EQAAEQMBoAhACxgHqZgAAAXZJREFURnc/jAcBEAABEDCdAISA6SMA9oMACIAACBhNAELA6O6H8SAAAiAAAqYTgBAwfQTAfhAAARAAAaMJQAgY3f0wHgRAAARAwHQCEAKmjwDYDwIgAAIgYDQBCAGjux/GgwAIgAAImE4AQsD0EQD7QQAEQAAEjCYAIWB098N4EAABEAAB0wlACJg AmA/CIAACICA0QQgBIzufhgPAiAAAiBgOgEIAdNHAOwHARAAARAwmgCEgNHdD NBAARAAARMJwAhYPoIgP0gAAIgAAJGE4AQMLr7YTwIgAAIgIDpBCAETB8BsB8EQAAEQMBoAhACRnc/jAcBEAABEDCdAISA6SMA9oMACIAACBhNAELA6O6H8SAAAiAAAqYTgBAwfQTAfhAAARAAAaMJQAgY3f0wHgRAAARAwHQCEAKmjwDYDwIgAAIgYDQBCAGjux/GgwAIgAAImE4AQsD0EQD7QQAEQAAEjCYAIWB098N4EAABEAAB0wn8f/4abES3u2YrAAAAAElFTkSuQmCC[/IMG][IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAgIAAAEnCAYAAADbzCvUAAAgAElEQVR4Xu2deWDUxfn/nw2VpggoCMopKIdBymGlIIpaK6IiEVoJVETk1spp5SzKkaQBBCEo gXLfVhBIipUFPCkKoT6q7UcKgVBDgsioiBiIMlvn93M7uxkPsdudrObzHv/UbKfz8w8r5nP53nPPM/MegoLCgsJHxAAARAAARAAASMJeCAEjOx3GA0CIAACIAACPgIQAhgIIAACIAACIGAwAQgBgzsfpoMACIAACIAAhADGAAiAAAiAAAgYTABCwODOh kgAAIgAAIgACGAMQACIAACIAACBhOAEDC482E6CIAACIAACEAIYAyAAAiAAAiAgMEEIAQM7nyYDgIgAAIgAAIhQuBoTluqlbbdFZUUmkDrCzKpkaurS3ZRnieb7qwyht46fa5YQR3arKItuT1KVkEZvPt8/n56/dlxNPGZt mLw8fo5A9EFZOrU8P6nSjr aV0z7UVw7Lq8Ibf0i 7vk31K2bRhtPjqW5Yd NiEAABEACBskpAuyJw/PBz1O/mB2n9vlCzKtJl1HfSmzRjXHOq vPSN/l//x1Kt1/7DH1yKli3iULgm/1Z9PubJtN7h85RZWpG097dSTf950pqOXS/D8zF1I7m7thK913tvo WDPBQv8VEDww9REueggxwTw5XggAIgEDZJmAZGngn00O3TAw1rjRXAXRYz3u20tAW7Wn DnOFwE e56lnvfvolcN BrWoGz2fv5aufil0NafX4L20ct6VrkZnnmcl9ajdm97537X01I5/Up8wBISrCnARCIAACIBAwhKwFAK6MAGEQPz78bMlV9M1/XfTj0VNEUKg boO1LDb 4G/93/kKC188lJXDf56cydq2nkT1TpfeuEeVw3DRSAAAiAAAjEnACEQc8TRrWDTJA91ygiWKYRAB88W tP1N9HCrZWo VVTaPnHoyjFZfhGhAV69NtNqxamRLfBKA0EQAAEQCChCUAIJHT3FG clRC4xROZIec86 mBK1Jp3f5mNPODXfTgdZGVg7tAAARAAATKJgEIgTLWb9EWAt9svYd edNLdDHCAmVsJKC5IAACIBAdAiUWAlZbDjmb/73tnekfi/vRiMxN9Om 7yjfu72tZYuHaPaqdOrQsIKlBcc W0jpY2fSC 9 St98R3RR1Ssp9d6FNGteMj0eRrKgKGfNP/bT0RNnfdvrrmryO5q06NmQ7XV22xO5kSO92Yk/Pv3LkCRF0fjxswopa2R4nZGX9/9oUfpoenr5J/TlweN02nt71Ytr05X1O9OwaROp152XU7JS5Jw0D43Msa6Hdw9EMqN/cYSHejxN1DXtn/TyqmvDMwRXgwAIgAAIlHkCJRYCTODrr8ZQarMZtO37II WN4 iO5IW0NNvnwwksIlv69MDtPrMErpO8XaFnp9o45MpdN 4/fTNeaLa3oz45/auoTsuP0irpnSmZ7Z2o/pHptLqXcF6dNsHCz2n6e/TrqG j/ XTp2/jIbO g9NfaQq7Vr5G rYd6vvbwMyP6Q5f76CLigq6txPe2j56Jtp6NyvQtpbk 6gpd9t8J5jQMTXTO/RlLI21KWug fT1PRO1LC6KMHdWDjyr8F0261/pV0niZpcNoTmv/sk/eYqop1v3k/3dHuRPveqgpT6I2nJh7OpXZ1gmbEQAiIs8PL hjT19S9oRCd3NuAqEAABEACB8kMgKkJAt62PEV3TKIsWbBtFtQ7cTzdet4r2SecB6bLa97zSgdqnve8TAT jSvRwxnGaM EXPtosEpb2T/btdZc/qhDg616fmEz3eBPqOLO XcpC2rSrP3n9OOV7dtPodlfT7FyiX1BDSn/1CxrVJVhagecIPX1PXRr5Umgdqb/7gHJy2nv/uIUebvVHapS hcZ1rRb2KDi2YyDdeP1Cn7O/gGrQnxd9TZP7Bot5ZZSHus3y/7uZ98Cml37MLJbwF83QwIl//YFatltFyedH0iv5s6l5hHkGYYPADSAAAiAAAglDIGZCoC6l0bKjq m3NYl0QqFjxzdo08bgFPScZxMNbNKJlv3Xz6YG3UoLjm6mrt77xeeHU l0a/1JISsPqhA4 fkAurbFooDoGDWtkGaMCZYhlsL5L9fUm0MbvhzuPSYp Mnz/J36Nu5Cf9sb/FtVakEzP/w31XutDr1W4TN6emLVsDuQRcj466 mGR9a23fs1dAtgLos/mgKASE8uniFzjqf0MEHBEAABEDANAIxEwKyg3ZzEJDYy37SuxrAnytpCL2UP5daSbNUN WIrXBchi5uLjtSPoHvmc 3Uq/God0ur0yIby6uXZt VTeb1niPMw5/LYBIzL4PF9kntv3J2f6qiOEQyov5S6idxCBaQkAIr9X/rU Zr3xJj6aaNvRhLwiAAAiAABNIGCGgOjjd4UVOQkD93kkIcPhh3DM/UMYfQwcDhwgyO9WlSZuCf7/A6/7H/t8JyngwsoHz2p89dNe04L06 1QhcCE1pSfe Ywevil4X7SEgKiLzhUXXJFZiLtAAARAAATKIoGEEQJqMlwkQsAp 1/XQUMn/khPT1Zz9IlUp8z3luRkRTf26epUdyVESwiIchAWKIuPLdoMAiAAAtEjUK6FQDJFvuytS07kFYQHJ39FcyPIEUgkISBWTpbuiJxP9IYgSgIBEAABEIgngYQRAnJsn4HU9iYbvpC/mm4KI0dAbIf72/4g0nDO3Fc74qu376RWt79OXxfF9fl7q62PTp2YSKEBsfJw7lzxHAQnO/A9CIAACIBA SKQMELg0wVXUbPBnwfo6hL5nHIECjzHvbH9miGx/RaVsmjD6fEU7g/r8u6Bfk3G0enWZ2jTmn0hZwuI7YThnCCgJkM2pTH0asF08h4hEPiouwZilSz44RMX0fXjvid150b5GtqwBgRAAARAwA2BhBECZ87 hTrWeow lA4lemDoIVryVNCF//D9LLqr6aP07rGgaer2QfXX Xg5v/fwnfRcdsPA4UF8Ny/9vzG5B311 yvUTzlfX5wnsKfldzRr0hbtdsInP/iEBoZxLr8qYnS7Bg4 fw1d3vvjgHG60/5KmiMgzlKYm1uDJi77mh7r7WaY4BoQAAEQAIHySsBSCLyT6aFbJoaabZUs5zRTd/pe1LLZW fd3jrFT zy/v3MzR/R0FsL6NDOafSH26bSx9/9RGfOBNvVhB6hF45Pp18VnfDHdT1yTXuaG/SnVNF7UkCXB56izCd/R82815389j2a/8de9HHlDbRsQYsQgcAiYFH/K2jFf5bT2qKtgrrthFYH/tgNFPlAIV3 gnzGQawOFPr yHBq3 j/6NRP9xXbmlheBznsAgEQAAEQsCZQTAjwTPmr/UvpwVsfpPX7Qm9kh9p30ps0Y1xzqir9xK3uiOHL6C6av/cV6npFBTryrwfolpuX U7UE58G1J WH59HN0pH9Ppm4n oS NXBcWAuJ7rvu/JuZS0KI0W7ixukHz4zpnvltN9bfvQy3v0hv MLqK7732FFqy8OXAmANv9vy9epoz D9KSd76j x/9mubOqOETCWcLllOPhn1o3aHQ8m5ov4hWvdGP6lZ2P8Q fa0rde79Kn3hPWK4ofecgGc/nU93XHWOPt4wkP7QY5WPUaOLBnpt/CvdLB0xzDWc/uENGtnhDlr472B9fELhQ5n/pif XKfY7xPoWvXP2ZfSr722/fY36 n1t 4KEUHurcCVIAACIAAC5YVAiBCw gEhnbFidaByTluqlbZdy4P38Q8eX5dmTd1s b36Qzn8OwG Hyqa/hbt ewEnfUu7deqdT2NmreahnT9jIZecxv9/X NqNn1janF1XfSDTdcT22urkO1618U4tTO5n158dRxOf3eQrhzVIcpVLKaVhKv35uWzq1q5y4HqrI5J5 X72rmo0odXikOORZWN0S/xOg0P3o0PctsvrtqP jz5BIwakxORHh/I9e72nGzam7A LH2/s1GZ8DwIgAAIgUD4JWIYGyqe5sAoEQAAEQAAEQEAmACGA8QACIAACIAACBhOAEDC482E6CIAACIAACEAIYAyAAAiAAAiAgMEEIAQM7nyYDgIgAAIgAAIQAhgDIAACIAACIGAwAQgBgzsfpoMACIAACIAAhADGAAiAAAiAAAgYTABCwODOh kgAAIgAAIgACGAMQACIAACIAACBhOAEDC482E6CIAACIAACEAIYAyAAAiAAAiAgMEEIAQM7nyYDgIgAAIgAAIQAhgDIAACIAACIGAwAQgBgzsfpoMACIAACIAAhADGAAiAAAiAAAgYTABCwODOh kgAAIgAAIgACGAMQACIAACIAACBhOAEDC482E6CIAACIAACEAIYAyAAAiAAAiAgMEEIAQM7nyYDgIgAAIgAAIQAhgDIAACIAACIGAwAQgBgzsfpoMACIAACIAAhADGAAiAAAiAAAgYTABCwODOh kgAAIgAAIgACGAMQACIAACIAACBhOAEDC482E6CIAACIAACEAIYAyAAAiAAAiAgMEEIAQM7nyYDgIgAAIgAAIQAhgDIAACIAACIGAwAQgBgzsfpoMACIAACIAAhADGAAiAAAiAAAgYTABCwODOh kgAAIgAAIgACGAMQACIAACIAACBhOAEDC482E6CIAACIAACEAIYAyAAAiAAAiAgMEEIAQM7nyYDgIgAAIgAAIQAhgDIAACIAACIGAwgYQSAqe27KFeM/IC3VG9dR1aml7N9 8Cz0EalPo9HSv6Vv6uLPafao woUFqI5o7KLksmmTbZrlvK RVoREbLqdbPETbVuyizNWF1HZIc3r89mARy7M odVbK/j UKnGJdSu8TF69/1k6prdlPo3cY/n7IF9dN wH4lHVVL BWHfr6tJtJm/E7ZcuOwQ/dCnnq1N7luNK0EABECg9AgklBDwO/wTlP7QEfrosNdLeD qY8xdtpd2tG8UljMoPZzh1yScSrSclFULcpcGHVX4rYzOHUIMOAkBweTa4VcQ5eyjj7 oSs1vPEk7PghfCHDLhRg4HwUhwG3L tvPAoJCCLpvXIib6FBEKSAAAiAQXQIJKQSeXHyGfth2MiAG5NlieRUCsnOMbhf7HWGfB39GfyyahUe7fLflCYecLzlN3b1iNUBdJXBbj3qdcNbHSygEhEjd/VMNylpUixoVVcTlP3RHId37mn VAx8QAAEQKEsEElIIzF5YSENu/S6wpCs7SQiB8IaXbsYaXgnRu9qNEJBXhBJVCPBqlRqaWpG5n pOaAghEL3hgpJAAARKiUDCCoFH 19CclyZ48Q8C/tGCQ2oeQWyaJC/4xd3x SDvrizWIZvvs0fn aPGoKQ48CxzEcQ9TitCOhyCmRHKbdX2PPU4K9D8ir47zpb5Hvrd61Fl/7zK99qjGjToanBeL3qnOV7deENOdaf8ruLaN/a70isCFRaGcr/qcFnQsJCwo52X38eyBewslm1S25XPW 9ed56S7oiwO1Rx5vduOHvdDZxOTIruW9jHSIqpfcKqgEBEChDBBJaCDBH1SEPaXwikCOgznaFw5KdguyI2Il0 jrU UxNOehLUNTFrf0vcr8z/UWMkvjcCgF5uXxkJX9SpWjzzUn RErRRi5z Y9X0pMdz9HOL/9Hk54MtU8dn/IsXDiiC14Mdf6CmxBkvCyuJvpxG9dICX3ie EshQ3BdgfzQcQ1uhUB2VEKISCXrfaRcNZiHEQ7D0MVXaFOPdQmFgLTJp lnpPq0KVSMmzQXn/fiRwDFkdTV1QOJFOWoXcJmgoCIFBGCSS8EGCusjOvcmll6ji2gTZZULygdUJAdQrCoYmXs qc/vVlRV9CWN m/he7GheOVn 7FQJyfeoS 81JxR2quF6XoGcnBFSnbcXtiqJdHPIsW a/OON0YDVCOG837ZaFgOoseccIlzXhDr 9uj7KXFyRVhYlm6r3R2NFQLBTk1qFGBDjhVdU5NUC XpZTKmiRfw7WmGRaI1TlAMCIFB CZQJIeC0dKq lEsmBEK3KYqud1q6j3SIhCsEdFvXOEFNN6vnbXaxEgJ1i7blyZn4om3s6DIW59H01FMhy/HREwLWfTTsjcq0pUgICGcavWTBg/ToxMo0e4p/Syt/5LHJ425xRmEgvCELAbnf7EI6otzyuo000ucE94EACMSOQJkQAmy 1RYweTlaxPyjJQRKY1ZmJwTYuavLyuwgZnY64kuk1GXfq862zT9Cwwi6rHbdLFyswiTmikBQCKh9ZLeiUNIVAXb6g /6ka6fHXqWgWBe2UIIqGJBnI3B41oWT/JOhNg98igZBEAABEIJJKAQOEhD 19Ajy4Mbs8STebZbe9phYE93LLTk2eCJREC7CiFExRLuFd4HXLGwFN003MNop4Vbhe/5nZsPls/ZJYp5znIOQLy9jUuU8SZ23/pP1CHRcPAeefp/U11aKpyYFEkQsBNjoCVmHCbI2AVGuCDh z6SCQhquGfkibi6XIVhDMXZwvoQgNqboRvjP3lUzrXI4V6VQweeCREDY/z8Z/WL5cHS EFDAIgkHgEEkoIyBnZVi9tefugGjLo0KMCvZdz1keZX6oiqU5gF1nr4uxCkU0uTiuUY7dyXkJJHYiu261OFlSvVWP2/L3cbv9y9GkaOeU8/fDPM4GTF4PL4sH8Adk uR4181/myNep3KySMVVOasjmkjaV6JS3jcyf25J2ywla qJ/1wZ/xAFC4jAp/hvbL 8akOuw6yP5u6reepOL2JQkxMN9JkTqB9LJh7pEU2FT8/uq0p6V3/tslj/yPfLph3xNLHepJN4rCC0CARCIN4GEEgLxhoH6QQAEQAAEQMA0AgklBFLv3pnQ/Ne92jyq7Ut0e6NqbAIVFmk/lnZ/RdrOBEKNpoAACJQBAhACYXRStF/Mpe1YwjC1XF8aaT Wdn9F2s5y3XkwDgRAIOoEEkoIRN06FAgCIAACIAACIGBLAEIAAwQEQAAEQAAEDCYAIWBw58N0EAABEAABEIAQwBgAARAAARAAAYMJQAgY3PkwHQRAAARAAAQgBDAGQAAEQAAEQMBgAhACBnc TAcBEAABEAABCAGMARAAARAAARAwmACEgMGdD9NBAARAAARAAEIAYwAEQAAEQAAEDCYAIWBw58N0EAABEAABEIAQwBgAARAAARAAAYMJQAgY3PkwHQRAAARAAAQgBDAGQAAEQAAEQMBgApZCoEfPHgZjgekgEF8CNWvWpGfmPhPfRqB2EAABIwhYCoEhQ4dQjRo1jYAAI0EgEQlMmTw5EZuFNoEACJQzAggNlLMOhTkgAAIgAAIgEA4BCIFwaOFaEAABEAABEChnBCAEylmHwhwQAAEQAAEQCIcAhEA4tHAtCIAACIAACJQzAhAC5axDYQ4IgAAIgAAIhEMAQiAcWrgWBEAABEAABMoZAQiBctahMAcEQAAEQAAEwiEAIRAOLVwLAiAAAiAAAuWMAIRAOetQmAMCIAACIAAC4RCAEAiHFq4FARAAARAAgXJGAEKgnHUozAEBEAABEACBcAhACIRDC9eCAAiAAAiAQDkjACFQzjoU5oAACIAACIBAOAQgBMKhhWtBAARAAARAoJwRgBAoZx0Kc0AABEAABEAgHAIQAuHQwrUgAAIgAAIgUM4IOAoBT5LH1uTCgsJyhgTmgAAIgAAIgIA5BGyFAIuAk/ ebUvj4laPEMSAOQMGloIACIAACJQvApZCwI0IEChYDOg ZUEgnNqyh7LPNKHHb49ux578fABd22IR7TtHVJma0cwPdtGD14XWMSfNQyNz9N 7uT/Pk013VhlDeSkraEtuD1cGnPdspaEt2tO7OybQ oJMaqTcdTSnLdVK207jZxVS1khXRZKdHaKTv8ZfXot5tWLUyxLditXaLeFNLbIiqRWXZos6oYK1EOX6/73h0FXAUCIAACZZOArRCYMaQ5DRo80Nayvz63wPKasrBasCJzP9Wd0JBusY AhNW77Mju8Ryn7CJHy47msZxQMbBpkoeGZ/gd2CVe0dAm5UMaXSQW3Nzv5Nx0DRYO9q3T50jnPLlNnTL8d7oVAnZ2CBGwM9nvfMW/v/21tRhwY5e4puI5ewHAdgib26Xn YQN98WaA0ExwO1/u5pf9Ihy67QqLhbCGgC4GARAAATKEAHHFQF29HYfO6HA945 ZmephQ5yl 2lHe0bUf8m7nqgwHOQHp1YmWZPqebuBpdXvTl DCVlPREQF8IZ1Uj7xDcb5n939jxHadIqATuk9A1 B R0v9wM1bG5aaLsvNUVAdVx2pXnZIeuLNlOu7Kt7BLOuk1v55UFLl tT25zv/bZlDXgTpq84KpAU/j6Phnd6Pn8tVEVh276BdeAAAiAQDwIOAqBSBslBMSL2y k3NzcmIuBswf2Ue Hz1Pn7KauhUCswgIqM3UmzMvvrdPqhjgb3d9EOXYz6XgKASc7bkgqHrrg9h69wTnsoLPLKazhxJ2/d1qVsOuHSJ8F3AcCIAACiUwgZkKAjWYxYCUECjwnKP2hI/RFzbo097bj1GtGno9TW284YnTKPrpv2I/Ef2mQ2ojmDkoOMGTnLa6tkFeFRmy4nCqt3EWZq4O7FyrVuISyFtWi4ytC/66WtWrJIWrTt16xOHm0O0ydOetm5DzTlcMDcht0M2/xfTyFgBs7RM4B5wbMHzuDuve nTa7yGfQ2SVWA9qOGE25c2b48i/UEAffNy3HP6MXQkSEBdwwc7tiEe0xgvJAAARAIF4EYiYE7FYEhAj46LA/MF 9dR1aml6Nlmd9Qqu3ViDhyC/1Ov37//Jzn7PnGD6LgKGbaviu5c82r6Of9VZ1n9Pna3tPK6SuRSsC6goBXzt1ReVAWRwWyP5rTfrTwKDIiFUnsDPsPn1UIEnNjQOV26LeL3 X6EKA2ypyD5yS pzs4nJ n9GMWnbsRss2ZlH9omTJI6fHaBMfrcIcVsx4tWBY877UesGnxRI7YzU2UC4IgAAIxJtAzIQAG Z2RUDn2Dl2zY5fOPe Tf0rCEI8CHBJ Rf4nH/a/0KFgAxWCAyxgsCi4vR7B2h17QauwwiRdhQ7l GNplPanmDMWScE2Nk3TjtdbHeB7n4nh nU1mjlCLixQyQ Pr77CN3bcjG5SfDj9uucta4 IQ50uzJ0QkBNYFQF1/DXljnuanDii 9BAARAoCwRiJkQcMoRkEMD4QiBCt1 qd3qJ4sGkSzIqwAcMuBww8hKwdWFm5NO0LTJZ6nnpDoxDwvM6d6AkkcdCJlhOsXW5R0MuvudhICc/c/Xqlv2whUC6hZAsR2y22H7XIcbk/xbFav39 cE2Dlh9aFxKwTsQiq6fACrHAEux23YItoPuBVfdbtptOtFeSAAAiDABGImBGK1InD8V41DcgZEN6pCgP thhXEv9t/uY mbKxDU6Xcg1gMB3lrmly LuZv5fjE1jar9sUzNOBkh85J8986ptSmVZozDJwEjq48p Q NeavK0PdrhmLsYAyQQAEQCBRCcRMCER7RYBn SJRkGf44gCg3KWH6Ic 9Yidu9g1cOH7h6jJFT/SlCeCOQMcHsh572JfjsCFy8PbZhhJ57EDWnAodIvbU91SqcXadb58B9lB6ZyT0/3cpnBm2KqTnZej34MvEvJ6TnfO7Ocy7ezQHQzkJhnPzi4WPqLtDYoOR7I7l0AVK6pw4u 7eN6j8fkvBbYLMoOx00fTfIeDjyIZF7gHBEAABBKNQMyEgN2KgC5Z8OGmXwUy/zmWf//4s7TkSW9auPcj8gBYDIjlfgFS7ATg5L9Bqd/TMe8XLBQm3BH8N197RZtK9MU/z5Cn4Gd0WbOqNG5G7ZiFBeST6uQOV0 tszqRz8398sE7XEctct77Lh8oxPeoJx6qIQW3p zZnSyo1ulUppNdTicVyrsGRIjF6pAitS7RV1YnQSbaw4v2gAAIgEA0CMRMCDitCESj8SgDBEAABEAABECgZARcCQFxjHAk/y2tA4VKhgF3gwAIgAAIgICZBBx/fZB/byDSD4sA/uhOFky9e2ekxcbkvnWvRm5nTBqEQkEABEAABECgFAjYCgGun3 FsG3bthE3hUUA379t67aIy8CNIAACIAACIAACsSHgKASEGIi0eoiASMnhPhAAARAAARCIPQFXQiD2zUANIAACIAACIAAC8SAAIRAP6qgTBEAABEAABBKEAIRAgnQEmgECIAACIAAC8SAAIRAP6qgTBEAABEAABBKEAIRAgnQEmgECIAACIAAC8SAAIRAP6qgTBEAABEAABBKEAIRAgnQEmgECIAACIAAC8SAAIRAP6qgTBEAABEAABBKEgKMQ4JMF7T6FBYUJYgqaAQIgAAIgAAIgEC4Bx98aOPnv2bZlXtzqEYIYCBc7rgcBEAABEACBxCDg6tcHnZrKYkD3SRSBcGrLHrr/Lz nERsuJ/Eb9U42ufm wHOQHp1YmWZPqVbscvm37q1 335OmodG5hDpvndzf54nm 6sMobyUlbQltwebppM5z1baWiL9vTujgm0viCTGil3Hc1pS7XSttP4WYWUNdJVkWRnh6hv/g5/WT367aZVC1NsC3Zrl6g3hfS2iEpklh3arCrGSpTD1 u d0cBV4EACIBA2SRgKwT4lwcHDR5oa5n4aWLdReV9tYAFRvaZJvT47aHWsyO7x3OcsoscLTuax3Ka0cwPdtGD1/mv3TTJQ8Mz/A7sks8HUJuUD2l00fdu7ndybrr EA72rdPnSOc8uU2dMvx3uhUCdnYIEbAz2e98xb //bW1GHBjl7im4jl7AcB2CJvbpef5hA33xZoDQTHA7X 7ml/0iHLrtCouFsrm441WgwAIgIAzAccVAXb0dh87ocD3jn5mZ0ShgxWZ 6nuhIZRncE74wjvCqs2vjl DCVlPRFou3BGNdI 8c2G d dPc9RmiIM0jf4HZDT/XIrVcfmxgLZeasrAqrjtCvPyQ5dWVy3sNOubK8WnJoAACAASURBVCu7hLNu09t5ZUEILrk uc392mdT1oA7afKCqwJN4fb1yehGz evTeix56afcQ0IgAAIuCHgKATcFKK7RgiIF7dfSPxTxOGECWK1lB pLbr77MIC6vXqTJiX31un1Q1xNrq/iXLsZtLxFAJOdtyQVDx0we09eoNz2EFnl1NYw4k7f0KmHXD9EcPygLBEAABBKFQMyEABvIYsBOCGxbsYsyVxdS9dZ1aEjjE7SjfSO64MVPaPXWCgE /N3S9Gq0PCv07229YQuxJH/2wD66b9iPlKdQbZDaiOYOSiauZ9Zb1SlrUS1fTJz/PXVFZRr6BtHfUk/RMe/fRD2iCLU /nuFvCqBPIPT7x2g1bUbUP8mzl2pzpx1M3Ke6crhAblU3cxbfB9PIeDGDpFzwLkB88fOoO69b6fNLvIZdHaJ1YC2I0ZT7pwZtO8cFQtx8H3TcvwzeiFERFjADTO3KxbOvY4rQAAEQKBsEIiZEHBaEWDnPWBKJUr3OudLvbH23tMKqWt2U59jFY5aJPepKwTspNf/91KfY7/Cm7A3KPV7 kWR0 dre83IIyEUhNioVOMS3/XHi8SH7Njb/MO6/puTTlD6Q0do9081AkKC71215BC16VuvWLKdrtvZGXafPiqQpObGgcrlqPfL3yW6EOC2itwDp6Q J7u4nN9nNKOWHbvRso1ZVL8oWfLI6THaxEerMIcVM14tGNa8L7Ve8Gkgl6NsPMZoJQiAAAhETiBmQoCbZLciIGbxraWZvTBDFQLi7wUev1P 6LCHhGOv6xUUvR8 T52LRAQv2cvCgO 1WhEQQoPbIpfBQmPz2fq lQhxP68giOu5juy/1qQ/DUx2JM/OZXij6ZS2Jxhz1gkBdvaN006HJBRy4br7nRymU6OilSPgxg6R Pj47iN0b8vF5CbBj9uvc9a6 oQ4kBMxhf06IaAmMKqCa/hryxx3NTjxxfcgAAIgUJYIxEwIOK0IMCR5 V1emtcJAb52zfvJvlWD5ttCl/plx6069UiEgJMwyF221xfGcBMWmNO9ASWPOhAyw3SKrctbHHX3OwkBOfufr1W37IUrBNQtgGK7Y7fD9rkONyb5typW7 /PCbBzwupD41YI2IVUdPkAVjkCXI7bsEW0H3ArvmKHSbTrQ3kgAAIgIBOImRDgSpxyBERD5FwBnoWrQkA3o5dj/mqOgJw/EIkQUEWKWH3g/AJelZg2 Sz1nFTHMSwgb02Toeti/laOT2xtsxq28QwNONmhc9L8t44ptWmV5gwDJ4GjK88puU N evKULdr4hUBAiAAAiYRiJkQcFoRYOc9ZGE1Wigtvz/7eW3fcrzICRj2RmX6eGEhdah41Jfcx0vzasyecwQeuqOQ7n3N rAgnbCQl/rVFQC fvmPV/oSDdUPXztlYx2aqvlOvpYd0IJDoVvcnuqWSi3WrvNtS5MdlM45Od3PdYUzw1ad7Lwc/R58kZDXc7pzZj XaWeH7mAgN8l4dnax8BFtb1B0OJLduQSqWFGFE3/fxfMejc9/KbBdkBmMnT6a5jscfGTSiwK2ggAIlF8CMRMCTisC7FBHZp2jw1 d99GVM/LFDP98/gW UECvisFdAUnev13evoD25 b77mGxsKUob0DuJlFepZX nQmijlt7naKNa/xX8jUD552nxcODOw54NWFkJX/CofrhXQh9fn7YMSwgn1Qnl6GeWmd1Ip bWDd7iOWuS8910 UIjvUU80VEMKbk/ZsztZUK3TqUwnu5xOKpR3DYgQi9UhRWpdoq sToIsv68BWAYCIGAygZgJAacVgWhBt9rPH05Cn9oWqxyA3KWH6Ic 9XDQTLQ6D WAAAiAAAjEnYArISCOEY7kv5EcKBQOFTXDX9wb6cmEumRDLtNtSCCctuNaEAABEAABEIg3AcdfH TfG4j0wyKAP7qTBVPv3hlpsYH71r3a3Ju8598uyIcCyR RMBhuPVymSF6Uy5MTBtUy R58QAAEQAAEQKAsErAVAmyQJ8lDbdu2jdg2FgF8/7at2yIuAzeCAAiAAAiAAAjEhoCjEBBiINLqIQIiJYf7QAAEQAAEQCD2BFwJgdg3AzWAAAiAAAiAAAjEgwCEQDyoo04QAAEQAAEQSBACEAIJ0hFoBgiAAAiAAAjEgwCEQDyoo04QAAEQAAEQSBACEAIJ0hFoBgiAAAiAAAjEgwCEQDyoo04QAAEQAAEQSBACEAIJ0hFoBgiAAAiAAAjEgwCEQDyoo04QAAEQAAEQSBACjkKATxa0 xQW H/ZDx8QAAEQAAEQAIGyR8DxtwZO/nu2rVUXt3qEIAbKXsejxSAAAiAAAiDABFz9 qATKhYDuk9JBEKB5wSlP3SEvqhZl5amV3NqQql z22bNvks9ZxUhxpZ1Cz/1r3V79vPSfPQyBwi3fdu7s/zZNOdVcZQXsoK2pLbwxWD856tNLRFe3p3xwRaX5BZrP1Hc9pSrbTtNH5WIWWNdFUk2dkh6pu/w19Wj367adXCFNuC3dol6k0hvS2iEpllhzarirES5fD1uu/dUcBVIAACIFA2CdgKAf7lwUGDB9paJn6aWHdRpKsFQgR8dNhD1VvXSTgh4PSTxOzI7vEcp wiR8uO5rGcZjTzg1304HV UpsmeWh4ht BXfL5AGqT8iGNLvrezf1Ozk3XH8LBvnX6HOmcJ7epU4b/TrdCwM4OIQJ2Jvudr/j3t7 2FgNu7BLXVDxnLwDYDmFzu/Q8n7DhvlhzICgGuP1vV/OLHlFunVbFxULZfLzRahAAARBwJuC4IsCO3u5jJxT43tHP7IwodFAaKwL8E8aPTqxMs6eEt KQu2wv7WjfiPo30ZN5c/wYSsp6gm4pSq8QzqhG2ie 2TD/u7PnOUpThEH6Br8DcrpfrlV1bM5dHipC1BUN1XHaledkh64sdrzCTruyrewSzrpNb eVBSG45PrkNvdrn01ZA 6kyQuuCjSF29cnoxs9n7820H9umOIaEAABECirBByFQKSGCQHx4vYLiX KONwwQWkIgeVZn9Dms/XDWnFwExZQmakzYV5 b51WN8TZ6P4myrGbScdTCDjZcUNS8dAFt/foDc5hB51dTmENJ 78vdOqhF0/RPos4D4QAAEQSGQCMRMCbDSLAZ0Q0C39b1uxizJXF1KlGpdQ1qJadIWUI9Ax SCt3lrBx7GtN1wx4Q5//oAcOrC7f 5tx6nXjDzp/oM0KPV7Oib1TJM7fkF7Xv RkvIvoK7ZTalv0 A1XOfjt/sv5rDAok vpIeL/u2mc9WZs7ycLmbkPNOVwwNyubqZt/g nkLAjR0i54BzA aPnUHde99Om13kM jsEqsBbUeMptw5M2jfOSoW4uD7puX4Z/RCiIiwgBtmblcs3PQ7rgEBEACBskAgZkLAaUVAN NnZz7rreohQoCdvXDEPINf835ykaMunkwo7s9cXJFWFgkF7gSRZ8D3r//vpcWEhkhGPLVlD/WeVugrn5f9OXTAgqGhJARylx6iH/rUC2vZmJ1h9 mjAklqbhyoPHjUXvEl0IcFtF7oFTUp TXVzO7zOaUcuO3WjZxiyqX5QseeT0GG3io1WYw4oZrxYMa96XWi/4NJDLURYeYrQRBEAABEpCIGZCgBtltSLA37kVAvKuAeGYf5HaiJ4afKbYrgKdkJDvd/reSQhwm2cvLKRH 1/imjk7l GNplPanmDMWScE2Nk3TjsdklDIlejud3KYTo3T1S/uCSdHwI0dIvHx8d1H6N6Wi8lNgh 3ReesdfUJcSAnYtrZoiYwqoJr GvLHHc1OPHF9yAAAiBQlgjETAhEa0UgVAj4VwGO/6pxXIQAC4XsM00CYQI3HT2newNKHnUgZIbpFFsXSYY h6i530kIyNn/fK26ZS9cIaBuARTbHbsdts91uDHJv1Wxen9/ToCdE1ZZuhUCdiEVXT6AVY4Al M2bOGm38O5xoqv2GESTlm4FgRAAATCJRAzIcANidWKAC/VizyBcGb8JV0RWJG5n pOaOg6LCBvTZM7Rhfzt3J8YmubVcfGMzTgZIfOSfPfOqbUplWaMwycBI6uPKfkPjXmrytD3a4Z7kOE60EABECgLBOImRBwWhFgaKEx 2ByHicMijj/7p9q GL6nFQnX6/4qieD4nAMr3WwkFcT/vGpg/4FtfAmD/lH1037AfqXVRToBIQOS2XjOyJp169wLXWw3ZAS04FLrF7aluqdRi7TqfkJAdlM45Od3PbQpnhq062Xk5 j34IiGv53TnzH4u084O3cFAbpLx7Oxi4SPa3qDocCS7cwlUsaIKJ/6 i c9Gp//UkDgMYOx00fTfIeDj8ryg4 2gwAIgIAgEDMh4LQiwN9zBj47Xs7nr5BXha7vdYo ese/a4Adtby7gK9XDxeyul XLPhw0698uxL4w3WN2HA5VVoZulNBiAOxQ6He7y6ivLXf ZIFR1ZyHxaQT6qTh5p6ap3ViXxu7pcP3uE6apHz3nf5QCG Rz3RUA0puD1lz 5kQbVOpzKd7HI6qVDeNSBCLFaHFKl1ib6yOgkSrw0QAAEQKI8EYiYE3KwIlEegsAkEQAAEQAAEyhIBV0JAHCMcyX8jPVCoLEFEW0EABEAABECgrBJw/PVB/r2BSD8sAvijO1kw9e6dkRabMPetezVyNgljBBoCAiAAAiBgNAFbIcBkPEneA33ato0YEosAvn/b1m0Rl4EbQQAEQAAEQAAEYkPAUQgIMRBp9RABkZLDfSAAAiAAAiAQewKuhEDsm4EaQAAEQAAEQAAE4kEAQiAe1FEnCIAACIAACCQIAQiBBOkINAMEQAAEQAAE4kEAQiAe1FEnCIAACIAACCQIAQiBBOkINAMEQAAEQAAE4kEAQiAe1FEnCIAACIAACCQIAQiBBOkINAMEQAAEQAAE4kEAQiAe1FEnCIAACIAACCQIAQiBBOkINAMEQAAEQAAE4kEAQiAe1FEnCIAACIAACCQIAQiBBOkINAMEQAAEQAAE4kEAQiAe1FEnCIAACIAACCQIAUsh0KNnjwRpIpoBAuYRqFmzJj0z9xnzDIfFIAACpU7AUggMGTqEatSoWeoNQoUgAAJ AlMmTwYKEAABEIg5AYQGYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hJwLQSO5rSlOQdzKWtk7I05 fkAurbFItp3jmj8rMKI68zzZNM9nuOUXZBJl0hl1qJu9Hz WrrF484WLqeL5z0an/ S5T1ym63Kn5PmoZE5/jrDsYvLHvl0F0p 9/c0f0ewzR3arKItuT18f D qZW23ff/XP/ACS9T5l IUmgCrffa38idqTG7ihn2aVuHXtjmb6/V57xnKw1t0T5gJ3Oa/Eg2ZQ24kyYvuCpm7UPBwTGUKGOmvPTJpkke6pSROM izJWfyzurjKG3TntfttKnMjWjmR/sogevK51eEIy4Nt34k9 v8nuvdFpX/mtxJQR4sHT2PEdppTgw3Dhfp 7Z/Hgn2nvXRupZfQB1TKlNq4ocIjvkeTnuHKR4UPJSVgScrlovD1K78oVze3eHv04WJe1TTtCzLsQIPyDDM4Jt5X/3ydALGW5H996302ZJHAx/bRmtWpjihKpUvhf9Yfdy4b5ZcyAocIR4Ckc4lYox5bQSHl8LDu1OmDETL8wsrBunnY6aM Tyuk8fZfkOiZedXK94x9VI yTQ7/zcTcsJb8IUqQ3M5jdpnQITFq77g6rBMcjvtTYpH9Jor/8Z0N4/UajeP/IJYqTtLM/3OQoB4cRe2VE6g0LALumDozpFuRP5OzeOmG0f1rwvfdnkDFWuvtH1y1Etn21pnVY3sAohmDoNZt1LWXWUsl3HVo gtZfPCah4vvboDbF7YMJdJWIuY6ePpvkWwkQnOJnV8EbTKW2P xWcRHxg2Y5RnV6lYW9kxX11xm41hsd76wWfRmUmGO74SMR i1abYv0slqSduucumkLIaRyo7zT53S/eld/ OigM L2YviE4WSiJ7bjXT8BRCPAsbkNBIT0/tXJYy klBVzSB epbqnUYu067VK OoPXtVWIgKuXv0C77v9DWC9HufwGRUvdO5ODA1co8HbpeZZhD50QcrrvzfFjKCnrCZ/N0VhRsetDt2JKLkMO1ehCFeKhl1nx/fPGjaHbpj2RsA7UzVhXZzlu7inta5z6J5z2RDI wim/LF0b62expCzUiQqXZ7fyGE59bsaBWhf/1q/gmMTpDYTYbCaRuuDRKwFQLcCby0/FTnPiFLNyIezXGkrI ep50PXOOL6epiO2Jpl PW93rj1tvfKO4QRXxKLP8KJ8wzk37t/TGs3NONQ5bpdLFkkb/gNPOUB5rVYBBCZEzn0GV/N4NHLl 37CYvdemWya2 1z2woj3MY LwLyhrzr2 Pwkh0b1BT19eghzzE23adfqugLgT4mVlYReaXRSjF7E4Nca5Xsp1EOVeucEfB 3RL6jcVTHn5qUgxpZdHFDOteD6Vi46Gcgr4H8vX/S6b8x82foOKti2LiTXRCemdPkdn/Tw53NwO97efrmvfBHascq30I31dSveCOS7cL/Y2SW347ZRo6lg5vqQcJycByKeNdEXunYKESrySuS EeNGtJnLm7dqIz02I3T52o51OONDN87VvBY1b0fHc83Ymb5cGDHuxPuB3yFy EiNfYvv5HcXx8DV zkfRcTMVV52cWy7vnOzumnVXu4nq 9EncfO eP54hlU 0XX7/J7TDcjZ8byfer7VnyntqHbYX uEvO 7P1gTpRdzoEcOv3t7/5Cxy8OfYfIYVyryYKb9zKusSZgKQTk5C41Ts3F8QBod/f7lP95ki92Ix4oMctVHaAYMD2nB5WeGDDswGWnIZzSssIaNLIoSY9fzGKZWy1LXSpyWg2Q4 g6NHJb3DzEchlqSMJqaUuO 6ttsMphsFPCXO/iDQvpkRH 0uTYevoj/rgaz7Tf3H7El/jYf9fFNPPqOoG8CSH6RD6BYMAPM8fr5o dUSwPQvSHCGFc/32zQB/plvTdCAExtjhZtOK50DwOdUwViy12b0D5kx j11tuoJ91W0tVqgVFgrzKINsqz0ZuTAqNP/J3r9XbQWfn3OMLD31/eKY2xus01t2sQKmzInUMyP ur Ts6NopBEib3v6Xqiou1dwX9ZlyZF0UdnIzPqyeMRGDviEpNBnXLc9ndx hB5p968u1kd8PwtnLzl8OzYn sLpfnoiwgNHl Mg5QW76zi5Ep7ZXff/I70l1MiBsedIr4p59fRkNrNfMl PBzyI/t LfVnlCumRB1WmLsWE3ljgpe5S3DQ8tu4zq/n1vQMC6Wdllm 7f9hvKn5dNci6WbhKl xscfMkJWAoBeSagm8mo4kCeaQnHI8d15DiUKhpUM7jsp799nuq9ttoXG5ZfFPz/rNhFYovqaFWHJpftZulTjcu7GciiDqvy1Ze43H7VdquBXtKwgCoi5KVqNWdBLGX2fOEg7T2y3bdEJ3PRxRR1eRFyAhDbqROUVkNYvHyEGNCFWGSbuE13N3zXV9zYfaH5BGq9IoRy9UuhCWGys SkJM5NONDiI7p77JeWMXOd0FP5OMU0rZZmRRxUdTTy9Sxe1HZatYnHHQt1WRiKXSeycBOCSBZPKmsWk GMD7mfnVa2WLRavTvYMYv3w5Wf/ceXc8HCSOzqEe8HOeymiiC7 zmspgo3u3Hr1HdOYQG759pq9UokzgkWw/9fF2p17H7fjhzup80/daEWv13n62ennA 7vuA cxpLYvn riWX0cVH7w8kKvO9uveEbtIjkoNVMar mNZu5Cyd1n SlBKwTUpXM1vqkqZtFBQnWfnxya6S6 F45hn5IJL MUZR 6sgl1 fM63wtYnpXLL8Vr9vi3GdZp5Q832CVkuUk6U5e/5HY5Za3bla qbrvtWXZhAassZquwgPySl1 u6gOqvgz437 c8B21qprhe7DV/lZn4sLJC8ele3mIVQp5R4DqHNTtqdzXv8/wL3vykqOwXwjJI6fHBDKN7V4Qsn3s/DncJcIJwtmJZV/Rz7qXkO6x1zkJmY8QMFaJobqXvSzMxFK1EL78LD6WE9zaZfWylGfA3G55XDFL9Xv5GZNZWrEOd3wIdlZjQ3zvhic7t7fOE/1piT pUX0/qKttqnCyu1 MZbFzIlxHrYpqpxVFO5FhxUL0nRBsIpFbiCAxq3azEuUUb9cJBfUdZbWCqXtPqM 8upNCbo/uXWhVV/lxyfGxpJgQYPhyZrfuwVUHmHyNeMGqil6eBTstcbPiTZ3/Is0e1NxHRZ6VyysV6n59Hni6sw50wsUNbjcPklDNTspbvIydditYKXQ75a4TbvJSpM7RC1Hmm02lzKOCKukBNa8 bCoHnTCUt/RwgumQF78MvKjF7EDMSHVnUejyNuR2s7jkHAT 6OKNdis3opxFhTfT0qKzDFRxpsbu1ZUh3Xixmy0Jx 0UDrGaUYotokLs8pka/NHFrdXtfjoHIvcp5xXIgkwXanNiLcdtncaHzM7OsbrlyeJfhBh17wfZNjWmrBNO8thR3xVWwpzrdeo7Xl0Qz8q4YWfpmtatiw0ju3eh p3OFvl9ojpepzHsZpndaSzJqzHquSzqe0I1XtcW/qs NWnLt5t OaUAIhQkCn4HQPrqxy1fiZmAEJISA6jxNaxiwZR9c07UN7nwzdxy8vnaoKWgyGSbuq0VdvLKJfnghdbRAP6ghv0uLecauLbc/SxfvENi6n2ZraFlXt60SA1aqEW1FhpaLVl4DVDEpdirR68XH8kEUbLysn3/syJV9SSLXeSaWUVybQWmULGT/Qb9Z nngpdvDGS2m490yJrhJv VwEnnFzvO/nMyvS494Y7sInxvi2CzqFBbgOed yaq/60pXHJc a7Q58EgzOnAtugdU5HdHGl70Jk9kuttGpZejG s 9SZS8UsJJbjqRqtolhC4Lk0Fe5/GHPid8oTB5qVs4CE5i1AlQXZnyKoI66 pw2zdUL8lDfTf4n7Fe9UJXDNSwn1qn3fj448a7fcmnYkVEdT7yM6WGFHU8f 1dzZBnkeL9MOqFQ74w1i3fBt8P4vmWtz5bvV/E/ZwczM5V/rcsPOTVNHVlRe27Xn2a vqnyQuP0pFBF9EfP xBvBoqb31TRbf8LpSfGTe26AQN15074CLtQV5qyEnnHJ3GktWKh AkvyfUJFu1bFV0ye9ucX6AuqMIDj06BHxCQF0SF8ujYrlUVCVmTfKs3GqWImYUvAy 1OsQ7m25OJD8xSpSPs3KLtOcBwsny4jldDUTWvydHzCx5US0V7xIxGxK/F3enWB3OIU6y1SFgFP58qzT7WltdoJBF7rQZaELZmyv7pRD0X/qrg/mou6SEHWu3OFfjubDmfjFKDKVeWlW5sDtEZndwmY1uU0dusyJTx1clnskZFyotlmtBjktv1oxVftPzoSWk8HsHjX5GdGNdTmrX4RqdDNkeeeMyLZWM93V8Ws3VmRW6tiT7ebvcrxJucO8YkMOtVixtloNtBofugNg5PGpru644amudvH7QYwV9RnRjSG7 0Xb5PvkNsnPk7qqJGfKi2eJnxVZgKr5ImoZdpn6drZYTQDkusX4Uet0OkXQbixZrcTJIs7uhEKZra4d6rtF9wxFxxWaXYrjOQK6l7bTcbtmIy2Z9VYrCiUrNb53z/Fm8yePOhCVQ2riawlqBwEQAIHyRyBsIeA0 yp/iErfIvWEwNJvQfRq1MX o1c6SgIBEAABECgpAddCwGnJraQNwf1BAuougLLIxik7vCzahDaDAAiAQHkk4FoIlEfjYRMIgAAIgAAImE4AQsD0EQD7QQAEQAAEjCYAIWB098N4EAABEAAB0wlACJg AmA/CIAACICA0QQgBIzufhgPAiAAAiBgOgEIAdNHAOwHARAAARAwmgCEgNHdD NBAARAAARMJwAhYPoIgP0gAAIgAAJGE4AQMLr7YTwIgAAIgIDpBCAETB8BsB8EQAAEQMBoAhACRnc/jAcBEAABEDCdAISA6SMA9oMACIAACBhNAELA6O6H8SAAAiAAAqYTgBAwfQTAfhAAARAAAaMJQAgY3f0wHgRAAARAwHQCEAKmjwDYDwIgAAIgYDQBCAGjux/GgwAIgAAImE4AQsD0EQD7QQAEQAAEjCYAIWB098N4EAABEAAB0wlACJg AmA/CIAACICA0QQgBIzufhgPAiAAAiBgOgEIAdNHAOwHARAAARAwmgCEgNHdD NBAARAAARMJwAhYPoIgP0gAAIgAAJGE4AQMLr7YTwIgAAIgIDpBCAETB8BsB8EQAAEQMBoAhACRnc/jAcBEAABEDCdAISA6SMA9oMACIAACBhNAELA6O6H8SAAAiAAAqYTgBAwfQTAfhAAARAAAaMJQAgY3f0wHgRAAARAwHQCEAKmjwDYDwIgAAIgYDQBCAGjux/GgwAIgAAImE4AQsD0EQD7QQAEQAAEjCYAIWB098N4EAABEAAB0wlACJg AmA/CIAACICA0QQgBIzufhgPAiAAAiBgOgEIAdNHAOwHARAAARAwmgCEgNHdD NBAARAAARMJwAhYPoIgP0gAAIgAAJGE4AQMLr7YTwIgAAIgIDpBCAETB8BsB8EQAAEQMBoAhACxgHqZgAAAXZJREFURnc/jAcBEAABEDCdAISA6SMA9oMACIAACBhNAELA6O6H8SAAAiAAAqYTgBAwfQTAfhAAARAAAaMJQAgY3f0wHgRAAARAwHQCEAKmjwDYDwIgAAIgYDQBCAGjux/GgwAIgAAImE4AQsD0EQD7QQAEQAAEjCYAIWB098N4EAABEAAB0wlACJg AmA/CIAACICA0QQgBIzufhgPAiAAAiBgOgEIAdNHAOwHARAAARAwmgCEgNHdD NBAARAAARMJwAhYPoIgP0gAAIgAAJGE4AQMLr7YTwIgAAIgIDpBCAETB8BsB8EQAAEQMBoAhACRnc/jAcBEAABEDCdAISA6SMA9oMACIAACBhNAELA6O6H8SAAAiAAAqYTgBAwfQTAfhAAARAAAaMJQAgY3f0wHgRAAARAwHQCEAKmjwDYDwIgAAIgYDQBCAGjux/GgwAIgAAImE4AQsD0EQD7QQAEQAAEjCYAIWB098N4EAABEAAB0wn8f/4abES3u2YrAAAAAElFTkSuQmCC[/IMG]
I've added the graphic of a http-based file directory of Ubuntu updates.  The image is not showing up for some reason.

I refuse to troubleshoot the troubleshooting system.
Are things falling apart at Canonical?
I've been away for years.[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAgIAAAEnCAYAAADbzCvUAAAgAElEQVR4Xu2deWDUxfn/nw2VpggoCMopKIdBymGlIIpaK6IiEVoJVETk1spp5SzKkaQBBCEo gXLfVhBIipUFPCkKoT6q7UcKgVBDgsioiBiIMlvn93M7uxkPsdudrObzHv/UbKfz8w8r5nP53nPPM/MegoLCgsJHxAAARAAARAAASMJeCAEjOx3GA0CIAACIAACPgIQAhgIIAACIAACIGAwAQgBgzsfpoMACIAACIAAhADGAAiAAAiAAAgYTABCwODOh kgAAIgAAIgACGAMQACIAACIAACBhOAEDC482E6CIAACIAACEAIYAyAAAiAAAiAgMEEIAQM7nyYDgIgAAIgAAIhQuBoTluqlbbdFZUUmkDrCzKpkaurS3ZRnieb7qwyht46fa5YQR3arKItuT1KVkEZvPt8/n56/dlxNPGZt mLw8fo5A9EFZOrU8P6nSjr aV0z7UVw7Lq8Ibf0i 7vk31K2bRhtPjqW5Yd NiEAABEACBskpAuyJw/PBz1O/mB2n9vlCzKtJl1HfSmzRjXHOq vPSN/l//x1Kt1/7DH1yKli3iULgm/1Z9PubJtN7h85RZWpG097dSTf950pqOXS/D8zF1I7m7thK913tvo WDPBQv8VEDww9REueggxwTw5XggAIgEDZJmAZGngn00O3TAw1rjRXAXRYz3u20tAW7Wn DnOFwE e56lnvfvolcN BrWoGz2fv5aufil0NafX4L20ct6VrkZnnmcl9ajdm97537X01I5/Up8wBISrCnARCIAACIBAwhKwFAK6MAGEQPz78bMlV9M1/XfTj0VNEUKg boO1LDb 4G/93/kKC188lJXDf56cydq2nkT1TpfeuEeVw3DRSAAAiAAAjEnACEQc8TRrWDTJA91ygiWKYRAB88W tP1N9HCrZWo VVTaPnHoyjFZfhGhAV69NtNqxamRLfBKA0EQAAEQCChCUAIJHT3FG clRC4xROZIec86 mBK1Jp3f5mNPODXfTgdZGVg7tAAARAAATKJgEIgTLWb9EWAt9svYd edNLdDHCAmVsJKC5IAACIBAdAiUWAlZbDjmb/73tnekfi/vRiMxN9Om 7yjfu72tZYuHaPaqdOrQsIKlBcc W0jpY2fSC 9 St98R3RR1Ssp9d6FNGteMj0eRrKgKGfNP/bT0RNnfdvrrmryO5q06NmQ7XV22xO5kSO92Yk/Pv3LkCRF0fjxswopa2R4nZGX9/9oUfpoenr5J/TlweN02nt71Ytr05X1O9OwaROp152XU7JS5Jw0D43Msa6Hdw9EMqN/cYSHejxN1DXtn/TyqmvDMwRXgwAIgAAIlHkCJRYCTODrr8ZQarMZtO37II WN4 iO5IW0NNvnwwksIlv69MDtPrMErpO8XaFnp9o45MpdN 4/fTNeaLa3oz45/auoTsuP0irpnSmZ7Z2o/pHptLqXcF6dNsHCz2n6e/TrqG j/ XTp2/jIbO g9NfaQq7Vr5G rYd6vvbwMyP6Q5f76CLigq6txPe2j56Jtp6NyvQtpbk 6gpd9t8J5jQMTXTO/RlLI21KWug fT1PRO1LC6KMHdWDjyr8F0261/pV0niZpcNoTmv/sk/eYqop1v3k/3dHuRPveqgpT6I2nJh7OpXZ1gmbEQAiIs8PL hjT19S9oRCd3NuAqEAABEACB8kMgKkJAt62PEV3TKIsWbBtFtQ7cTzdet4r2SecB6bLa97zSgdqnve8TAT jSvRwxnGaM EXPtosEpb2T/btdZc/qhDg616fmEz3eBPqOLO XcpC2rSrP3n9OOV7dtPodlfT7FyiX1BDSn/1CxrVJVhagecIPX1PXRr5Umgdqb/7gHJy2nv/uIUebvVHapS hcZ1rRb2KDi2YyDdeP1Cn7O/gGrQnxd9TZP7Bot5ZZSHus3y/7uZ98Cml37MLJbwF83QwIl//YFatltFyedH0iv5s6l5hHkGYYPADSAAAiAAAglDIGZCoC6l0bKjq m3NYl0QqFjxzdo08bgFPScZxMNbNKJlv3Xz6YG3UoLjm6mrt77xeeHU l0a/1JISsPqhA4 fkAurbFooDoGDWtkGaMCZYhlsL5L9fUm0MbvhzuPSYp Mnz/J36Nu5Cf9sb/FtVakEzP/w31XutDr1W4TN6emLVsDuQRcj466 mGR9a23fs1dAtgLos/mgKASE8uniFzjqf0MEHBEAABEDANAIxEwKyg3ZzEJDYy37SuxrAnytpCL2UP5daSbNUN WIrXBchi5uLjtSPoHvmc 3Uq/God0ur0yIby6uXZt VTeb1niPMw5/LYBIzL4PF9kntv3J2f6qiOEQyov5S6idxCBaQkAIr9X/rU Zr3xJj6aaNvRhLwiAAAiAABNIGCGgOjjd4UVOQkD93kkIcPhh3DM/UMYfQwcDhwgyO9WlSZuCf7/A6/7H/t8JyngwsoHz2p89dNe04L06 1QhcCE1pSfe Ywevil4X7SEgKiLzhUXXJFZiLtAAARAAATKIoGEEQJqMlwkQsAp 1/XQUMn/khPT1Zz9IlUp8z3luRkRTf26epUdyVESwiIchAWKIuPLdoMAiAAAtEjUK6FQDJFvuytS07kFYQHJ39FcyPIEUgkISBWTpbuiJxP9IYgSgIBEAABEIgngYQRAnJsn4HU9iYbvpC/mm4KI0dAbIf72/4g0nDO3Fc74qu376RWt79OXxfF9fl7q62PTp2YSKEBsfJw7lzxHAQnO/A9CIAACIBA SKQMELg0wVXUbPBnwfo6hL5nHIECjzHvbH9miGx/RaVsmjD6fEU7g/r8u6Bfk3G0enWZ2jTmn0hZwuI7YThnCCgJkM2pTH0asF08h4hEPiouwZilSz44RMX0fXjvid150b5GtqwBgRAAARAwA2BhBECZ87 hTrWeow lA4lemDoIVryVNCF//D9LLqr6aP07rGgaer2QfXX Xg5v/fwnfRcdsPA4UF8Ny/9vzG5B311 yvUTzlfX5wnsKfldzRr0hbtdsInP/iEBoZxLr8qYnS7Bg4 fw1d3vvjgHG60/5KmiMgzlKYm1uDJi77mh7r7WaY4BoQAAEQAIHySsBSCLyT6aFbJoaabZUs5zRTd/pe1LLZW fd3jrFT zy/v3MzR/R0FsL6NDOafSH26bSx9/9RGfOBNvVhB6hF45Pp18VnfDHdT1yTXuaG/SnVNF7UkCXB56izCd/R82815389j2a/8de9HHlDbRsQYsQgcAiYFH/K2jFf5bT2qKtgrrthFYH/tgNFPlAIV3 gnzGQawOFPr yHBq3 j/6NRP9xXbmlheBznsAgEQAAEQsCZQTAjwTPmr/UvpwVsfpPX7Qm9kh9p30ps0Y1xzqir9xK3uiOHL6C6av/cV6npFBTryrwfolpuX U7UE58G1J WH59HN0pH9Ppm4n oS NXBcWAuJ7rvu/JuZS0KI0W7ixukHz4zpnvltN9bfvQy3v0hv MLqK7732FFqy8OXAmANv9vy9epoz D9KSd76j x/9mubOqOETCWcLllOPhn1o3aHQ8m5ov4hWvdGP6lZ2P8Q fa0rde79Kn3hPWK4ofecgGc/nU93XHWOPt4wkP7QY5WPUaOLBnpt/CvdLB0xzDWc/uENGtnhDlr472B9fELhQ5n/pif XKfY7xPoWvXP2ZfSr722/fY36 n1t 4KEUHurcCVIAACIAAC5YVAiBCw gEhnbFidaByTluqlbZdy4P38Q8eX5dmTd1s b36Qzn8OwG Hyqa/hbt ewEnfUu7deqdT2NmreahnT9jIZecxv9/X NqNn1janF1XfSDTdcT22urkO1618U4tTO5n158dRxOf3eQrhzVIcpVLKaVhKv35uWzq1q5y4HqrI5J5 X72rmo0odXikOORZWN0S/xOg0P3o0PctsvrtqP jz5BIwakxORHh/I9e72nGzam7A LH2/s1GZ8DwIgAAIgUD4JWIYGyqe5sAoEQAAEQAAEQEAmACGA8QACIAACIAACBhOAEDC482E6CIAACIAACEAIYAyAAAiAAAiAgMEEIAQM7nyYDgIgAAIgAAIQAhgDIAACIAACIGAwAQgBgzsfpoMACIAACIAAhADGAAiAAAiAAAgYTABCwODOh kgAAIgAAIgACGAMQACIAACIAACBhOAEDC482E6CIAACIAACEAIYAyAAAiAAAiAgMEEIAQM7nyYDgIgAAIgAAIQAhgDIAACIAACIGAwAQgBgzsfpoMACIAACIAAhADGAAiAAAiAAAgYTABCwODOh kgAAIgAAIgACGAMQACIAACIAACBhOAEDC482E6CIAACIAACEAIYAyAAAiAAAiAgMEEIAQM7nyYDgIgAAIgAAIQAhgDIAACIAACIGAwAQgBgzsfpoMACIAACIAAhADGAAiAAAiAAAgYTABCwODOh kgAAIgAAIgACGAMQACIAACIAACBhOAEDC482E6CIAACIAACEAIYAyAAAiAAAiAgMEEIAQM7nyYDgIgAAIgAAIQAhgDIAACIAACIGAwAQgBgzsfpoMACIAACIAAhADGAAiAAAiAAAgYTABCwODOh kgAAIgAAIgACGAMQACIAACIAACBhOAEDC482E6CIAACIAACEAIYAyAAAiAAAiAgMEEIAQM7nyYDgIgAAIgAAIQAhgDIAACIAACIGAwgYQSAqe27KFeM/IC3VG9dR1aml7N9 8Cz0EalPo9HSv6Vv6uLPafao woUFqI5o7KLksmmTbZrlvK RVoREbLqdbPETbVuyizNWF1HZIc3r89mARy7M odVbK/j UKnGJdSu8TF69/1k6prdlPo3cY/n7IF9dN wH4lHVVL BWHfr6tJtJm/E7ZcuOwQ/dCnnq1N7luNK0EABECg9AgklBDwO/wTlP7QEfrosNdLeD qY8xdtpd2tG8UljMoPZzh1yScSrSclFULcpcGHVX4rYzOHUIMOAkBweTa4VcQ5eyjj7 oSs1vPEk7PghfCHDLhRg4HwUhwG3L tvPAoJCCLpvXIib6FBEKSAAAiAQXQIJKQSeXHyGfth2MiAG5NlieRUCsnOMbhf7HWGfB39GfyyahUe7fLflCYecLzlN3b1iNUBdJXBbj3qdcNbHSygEhEjd/VMNylpUixoVVcTlP3RHId37mn VAx8QAAEQKEsEElIIzF5YSENu/S6wpCs7SQiB8IaXbsYaXgnRu9qNEJBXhBJVCPBqlRqaWpG5n pOaAghEL3hgpJAAARKiUDCCoFH 19CclyZ48Q8C/tGCQ2oeQWyaJC/4xd3x SDvrizWIZvvs0fn aPGoKQ48CxzEcQ9TitCOhyCmRHKbdX2PPU4K9D8ir47zpb5Hvrd61Fl/7zK99qjGjToanBeL3qnOV7deENOdaf8ruLaN/a70isCFRaGcr/qcFnQsJCwo52X38eyBewslm1S25XPW 9ed56S7oiwO1Rx5vduOHvdDZxOTIruW9jHSIqpfcKqgEBEChDBBJaCDBH1SEPaXwikCOgznaFw5KdguyI2Il0 jrU UxNOehLUNTFrf0vcr8z/UWMkvjcCgF5uXxkJX9SpWjzzUn RErRRi5z Y9X0pMdz9HOL/9Hk54MtU8dn/IsXDiiC14Mdf6CmxBkvCyuJvpxG9dICX3ie EshQ3BdgfzQcQ1uhUB2VEKISCXrfaRcNZiHEQ7D0MVXaFOPdQmFgLTJp lnpPq0KVSMmzQXn/fiRwDFkdTV1QOJFOWoXcJmgoCIFBGCSS8EGCusjOvcmll6ji2gTZZULygdUJAdQrCoYmXs qc/vVlRV9CWN m/he7GheOVn 7FQJyfeoS 81JxR2quF6XoGcnBFSnbcXtiqJdHPIsW a/OON0YDVCOG837ZaFgOoseccIlzXhDr 9uj7KXFyRVhYlm6r3R2NFQLBTk1qFGBDjhVdU5NUC XpZTKmiRfw7WmGRaI1TlAMCIFB CZQJIeC0dKq lEsmBEK3KYqud1q6j3SIhCsEdFvXOEFNN6vnbXaxEgJ1i7blyZn4om3s6DIW59H01FMhy/HREwLWfTTsjcq0pUgICGcavWTBg/ToxMo0e4p/Syt/5LHJ425xRmEgvCELAbnf7EI6otzyuo000ucE94EACMSOQJkQAmy 1RYweTlaxPyjJQRKY1ZmJwTYuavLyuwgZnY64kuk1GXfq862zT9Cwwi6rHbdLFyswiTmikBQCKh9ZLeiUNIVAXb6g /6ka6fHXqWgWBe2UIIqGJBnI3B41oWT/JOhNg98igZBEAABEIJJKAQOEhD 19Ajy4Mbs8STebZbe9phYE93LLTk2eCJREC7CiFExRLuFd4HXLGwFN003MNop4Vbhe/5nZsPls/ZJYp5znIOQLy9jUuU8SZ23/pP1CHRcPAeefp/U11aKpyYFEkQsBNjoCVmHCbI2AVGuCDh z6SCQhquGfkibi6XIVhDMXZwvoQgNqboRvjP3lUzrXI4V6VQweeCREDY/z8Z/WL5cHS EFDAIgkHgEEkoIyBnZVi9tefugGjLo0KMCvZdz1keZX6oiqU5gF1nr4uxCkU0uTiuUY7dyXkJJHYiu261OFlSvVWP2/L3cbv9y9GkaOeU8/fDPM4GTF4PL4sH8Adk uR4181/myNep3KySMVVOasjmkjaV6JS3jcyf25J2ywla qJ/1wZ/xAFC4jAp/hvbL 8akOuw6yP5u6reepOL2JQkxMN9JkTqB9LJh7pEU2FT8/uq0p6V3/tslj/yPfLph3xNLHepJN4rCC0CARCIN4GEEgLxhoH6QQAEQAAEQMA0AgklBFLv3pnQ/Ne92jyq7Ut0e6NqbAIVFmk/lnZ/RdrOBEKNpoAACJQBAhACYXRStF/Mpe1YwjC1XF8aaT Wdn9F2s5y3XkwDgRAIOoEEkoIRN06FAgCIAACIAACIGBLAEIAAwQEQAAEQAAEDCYAIWBw58N0EAABEAABEIAQwBgAARAAARAAAYMJQAgY3PkwHQRAAARAAAQgBDAGQAAEQAAEQMBgAhACBnc TAcBEAABEAABCAGMARAAARAAARAwmACEgMGdD9NBAARAAARAAEIAYwAEQAAEQAAEDCYAIWBw58N0EAABEAABEIAQwBgAARAAARAAAYMJQAgY3PkwHQRAAARAAAQgBDAGQAAEQAAEQMBgApZCoEfPHgZjgekgEF8CNWvWpGfmPhPfRqB2EAABIwhYCoEhQ4dQjRo1jYAAI0EgEQlMmTw5EZuFNoEACJQzAggNlLMOhTkgAAIgAAIgEA4BCIFwaOFaEAABEAABEChnBCAEylmHwhwQAAEQAAEQCIcAhEA4tHAtCIAACIAACJQzAhAC5axDYQ4IgAAIgAAIhEMAQiAcWrgWBEAABEAABMoZAQiBctahMAcEQAAEQAAEwiEAIRAOLVwLAiAAAiAAAuWMAIRAOetQmAMCIAACIAAC4RCAEAiHFq4FARAAARAAgXJGAEKgnHUozAEBEAABEACBcAhACIRDC9eCAAiAAAiAQDkjACFQzjoU5oAACIAACIBAOAQgBMKhhWtBAARAAARAoJwRgBAoZx0Kc0AABEAABEAgHAIQAuHQwrUgAAIgAAIgUM4IOAoBT5LH1uTCgsJyhgTmgAAIgAAIgIA5BGyFAIuAk/ ebUvj4laPEMSAOQMGloIACIAACJQvApZCwI0IEChYDOg ZUEgnNqyh7LPNKHHb49ux578fABd22IR7TtHVJma0cwPdtGD14XWMSfNQyNz9N 7uT/Pk013VhlDeSkraEtuD1cGnPdspaEt2tO7OybQ oJMaqTcdTSnLdVK207jZxVS1khXRZKdHaKTv8ZfXot5tWLUyxLditXaLeFNLbIiqRWXZos6oYK1EOX6/73h0FXAUCIAACZZOArRCYMaQ5DRo80Nayvz63wPKasrBasCJzP9Wd0JBusY AhNW77Mju8Ryn7CJHy47msZxQMbBpkoeGZ/gd2CVe0dAm5UMaXSQW3Nzv5Nx0DRYO9q3T50jnPLlNnTL8d7oVAnZ2CBGwM9nvfMW/v/21tRhwY5e4puI5ewHAdgib26Xn YQN98WaA0ExwO1/u5pf9Ihy67QqLhbCGgC4GARAAATKEAHHFQF29HYfO6HA945 ZmephQ5yl 2lHe0bUf8m7nqgwHOQHp1YmWZPqebuBpdXvTl DCVlPREQF8IZ1Uj7xDcb5n939jxHadIqATuk9A1 B R0v9wM1bG5aaLsvNUVAdVx2pXnZIeuLNlOu7Kt7BLOuk1v55UFLl tT25zv/bZlDXgTpq84KpAU/j6Phnd6Pn8tVEVh276BdeAAAiAQDwIOAqBSBslBMSL2y k3NzcmIuBswf2Ue Hz1Pn7KauhUCswgIqM3UmzMvvrdPqhjgb3d9EOXYz6XgKASc7bkgqHrrg9h69wTnsoLPLKazhxJ2/d1qVsOuHSJ8F3AcCIAACiUwgZkKAjWYxYCUECjwnKP2hI/RFzbo097bj1GtGno9TW284YnTKPrpv2I/Ef2mQ2ojmDkoOMGTnLa6tkFeFRmy4nCqt3EWZq4O7FyrVuISyFtWi4ytC/66WtWrJIWrTt16xOHm0O0ydOetm5DzTlcMDcht0M2/xfTyFgBs7RM4B5wbMHzuDuve nTa7yGfQ2SVWA9qOGE25c2b48i/UEAffNy3HP6MXQkSEBdwwc7tiEe0xgvJAAARAIF4EYiYE7FYEhAj46LA/MF 9dR1aml6Nlmd9Qqu3ViDhyC/1Ov37//Jzn7PnGD6LgKGbaviu5c82r6Of9VZ1n9Pna3tPK6SuRSsC6goBXzt1ReVAWRwWyP5rTfrTwKDIiFUnsDPsPn1UIEnNjQOV26LeL3 X6EKA2ypyD5yS pzs4nJ n9GMWnbsRss2ZlH9omTJI6fHaBMfrcIcVsx4tWBY877UesGnxRI7YzU2UC4IgAAIxJtAzIQAG Z2RUDn2Dl2zY5fOPe Tf0rCEI8CHBJ Rf4nH/a/0KFgAxWCAyxgsCi4vR7B2h17QauwwiRdhQ7l GNplPanmDMWScE2Nk3TjtdbHeB7n4nh nU1mjlCLixQyQ Pr77CN3bcjG5SfDj9uucta4 IQ50uzJ0QkBNYFQF1/DXljnuanDii 9BAARAoCwRiJkQcMoRkEMD4QiBCt1 qd3qJ4sGkSzIqwAcMuBww8hKwdWFm5NO0LTJZ6nnpDoxDwvM6d6AkkcdCJlhOsXW5R0MuvudhICc/c/Xqlv2whUC6hZAsR2y22H7XIcbk/xbFav39 cE2Dlh9aFxKwTsQiq6fACrHAEux23YItoPuBVfdbtptOtFeSAAAiDABGImBGK1InD8V41DcgZEN6pCgP thhXEv9t/uY mbKxDU6Xcg1gMB3lrmly LuZv5fjE1jar9sUzNOBkh85J8986ptSmVZozDJwEjq48p Q NeavK0PdrhmLsYAyQQAEQCBRCcRMCER7RYBn SJRkGf44gCg3KWH6Ic 9Yidu9g1cOH7h6jJFT/SlCeCOQMcHsh572JfjsCFy8PbZhhJ57EDWnAodIvbU91SqcXadb58B9lB6ZyT0/3cpnBm2KqTnZej34MvEvJ6TnfO7Ocy7ezQHQzkJhnPzi4WPqLtDYoOR7I7l0AVK6pw4u 7eN6j8fkvBbYLMoOx00fTfIeDjyIZF7gHBEAABBKNQMyEgN2KgC5Z8OGmXwUy/zmWf//4s7TkSW9auPcj8gBYDIjlfgFS7ATg5L9Bqd/TMe8XLBQm3BH8N197RZtK9MU/z5Cn4Gd0WbOqNG5G7ZiFBeST6uQOV0 tszqRz8398sE7XEctct77Lh8oxPeoJx6qIQW3p zZnSyo1ulUppNdTicVyrsGRIjF6pAitS7RV1YnQSbaw4v2gAAIgEA0CMRMCDitCESj8SgDBEAABEAABECgZARcCQFxjHAk/y2tA4VKhgF3gwAIgAAIgICZBBx/fZB/byDSD4sA/uhOFky9e2ekxcbkvnWvRm5nTBqEQkEABEAABECgFAjYCgGun3 FsG3bthE3hUUA379t67aIy8CNIAACIAACIAACsSHgKASEGIi0eoiASMnhPhAAARAAARCIPQFXQiD2zUANIAACIAACIAAC8SAAIRAP6qgTBEAABEAABBKEAIRAgnQEmgECIAACIAAC8SAAIRAP6qgTBEAABEAABBKEAIRAgnQEmgECIAACIAAC8SAAIRAP6qgTBEAABEAABBKEAIRAgnQEmgECIAACIAAC8SAAIRAP6qgTBEAABEAABBKEgKMQ4JMF7T6FBYUJYgqaAQIgAAIgAAIgEC4Bx98aOPnv2bZlXtzqEYIYCBc7rgcBEAABEACBxCDg6tcHnZrKYkD3SRSBcGrLHrr/Lz nERsuJ/Eb9U42ufm wHOQHp1YmWZPqVbscvm37q1 335OmodG5hDpvndzf54nm 6sMobyUlbQltwebppM5z1baWiL9vTujgm0viCTGil3Hc1pS7XSttP4WYWUNdJVkWRnh6hv/g5/WT367aZVC1NsC3Zrl6g3hfS2iEpklh3arCrGSpTD1 u d0cBV4EACIBA2SRgKwT4lwcHDR5oa5n4aWLdReV9tYAFRvaZJvT47aHWsyO7x3OcsoscLTuax3Ka0cwPdtGD1/mv3TTJQ8Mz/A7sks8HUJuUD2l00fdu7ndybrr EA72rdPnSOc8uU2dMvx3uhUCdnYIEbAz2e98xb //bW1GHBjl7im4jl7AcB2CJvbpef5hA33xZoDQTHA7X 7ml/0iHLrtCouFsrm441WgwAIgIAzAccVAXb0dh87ocD3jn5mZ0ShgxWZ 6nuhIZRncE74wjvCqs2vjl DCVlPRFou3BGNdI 8c2G d dPc9RmiIM0jf4HZDT/XIrVcfmxgLZeasrAqrjtCvPyQ5dWVy3sNOubK8WnJoAACAASURBVCu7hLNu09t5ZUEILrk uc392mdT1oA7afKCqwJN4fb1yehGz evTeix56afcQ0IgAAIuCHgKATcFKK7RgiIF7dfSPxTxOGECWK1lB pLbr77MIC6vXqTJiX31un1Q1xNrq/iXLsZtLxFAJOdtyQVDx0we09eoNz2EFnl1NYw4k7f0KmHXD9EcPygLBEAABBKFQMyEABvIYsBOCGxbsYsyVxdS9dZ1aEjjE7SjfSO64MVPaPXWCgE /N3S9Gq0PCv07229YQuxJH/2wD66b9iPlKdQbZDaiOYOSiauZ9Zb1SlrUS1fTJz/PXVFZRr6BtHfUk/RMe/fRD2iCLU /nuFvCqBPIPT7x2g1bUbUP8mzl2pzpx1M3Ke6crhAblU3cxbfB9PIeDGDpFzwLkB88fOoO69b6fNLvIZdHaJ1YC2I0ZT7pwZtO8cFQtx8H3TcvwzeiFERFjADTO3KxbOvY4rQAAEQKBsEIiZEHBaEWDnPWBKJUr3OudLvbH23tMKqWt2U59jFY5aJPepKwTspNf/91KfY7/Cm7A3KPV7 kWR0 dre83IIyEUhNioVOMS3/XHi8SH7Njb/MO6/puTTlD6Q0do9081AkKC71215BC16VuvWLKdrtvZGXafPiqQpObGgcrlqPfL3yW6EOC2itwDp6Q J7u4nN9nNKOWHbvRso1ZVL8oWfLI6THaxEerMIcVM14tGNa8L7Ve8Gkgl6NsPMZoJQiAAAhETiBmQoCbZLciIGbxraWZvTBDFQLi7wUev1P 6LCHhGOv6xUUvR8 T52LRAQv2cvCgO 1WhEQQoPbIpfBQmPz2fq lQhxP68giOu5juy/1qQ/DUx2JM/OZXij6ZS2Jxhz1gkBdvaN006HJBRy4br7nRymU6OilSPgxg6R Pj47iN0b8vF5CbBj9uvc9a6 oQ4kBMxhf06IaAmMKqCa/hryxx3NTjxxfcgAAIgUJYIxEwIOK0IMCR5 V1emtcJAb52zfvJvlWD5ttCl/plx6069UiEgJMwyF221xfGcBMWmNO9ASWPOhAyw3SKrctbHHX3OwkBOfufr1W37IUrBNQtgGK7Y7fD9rkONyb5typW7 /PCbBzwupD41YI2IVUdPkAVjkCXI7bsEW0H3ArvmKHSbTrQ3kgAAIgIBOImRDgSpxyBERD5FwBnoWrQkA3o5dj/mqOgJw/EIkQUEWKWH3g/AJelZg2 Sz1nFTHMSwgb02Toeti/laOT2xtsxq28QwNONmhc9L8t44ptWmV5gwDJ4GjK88puU N evKULdr4hUBAiAAAiYRiJkQcFoRYOc9ZGE1Wigtvz/7eW3fcrzICRj2RmX6eGEhdah41Jfcx0vzasyecwQeuqOQ7n3N rAgnbCQl/rVFQC fvmPV/oSDdUPXztlYx2aqvlOvpYd0IJDoVvcnuqWSi3WrvNtS5MdlM45Od3PdYUzw1ad7Lwc/R58kZDXc7pzZj XaWeH7mAgN8l4dnax8BFtb1B0OJLduQSqWFGFE3/fxfMejc9/KbBdkBmMnT6a5jscfGTSiwK2ggAIlF8CMRMCTisC7FBHZp2jw1 d99GVM/LFDP98/gW UECvisFdAUnev13evoD25 b77mGxsKUob0DuJlFepZX nQmijlt7naKNa/xX8jUD552nxcODOw54NWFkJX/CofrhXQh9fn7YMSwgn1Qnl6GeWmd1Ip bWDd7iOWuS8910 UIjvUU80VEMKbk/ZsztZUK3TqUwnu5xOKpR3DYgQi9UhRWpdoq sToIsv68BWAYCIGAygZgJAacVgWhBt9rPH05Cn9oWqxyA3KWH6Ic 9XDQTLQ6D WAAAiAAAjEnYArISCOEY7kv5EcKBQOFTXDX9wb6cmEumRDLtNtSCCctuNaEAABEAABEIg3AcdfH TfG4j0wyKAP7qTBVPv3hlpsYH71r3a3Ju8598uyIcCyR RMBhuPVymSF6Uy5MTBtUy R58QAAEQAAEQKAsErAVAmyQJ8lDbdu2jdg2FgF8/7at2yIuAzeCAAiAAAiAAAjEhoCjEBBiINLqIQIiJYf7QAAEQAAEQCD2BFwJgdg3AzWAAAiAAAiAAAjEgwCEQDyoo04QAAEQAAEQSBACEAIJ0hFoBgiAAAiAAAjEgwCEQDyoo04QAAEQAAEQSBACEAIJ0hFoBgiAAAiAAAjEgwCEQDyoo04QAAEQAAEQSBACEAIJ0hFoBgiAAAiAAAjEgwCEQDyoo04QAAEQAAEQSBACjkKATxa0 xQW H/ZDx8QAAEQAAEQAIGyR8DxtwZO/nu2rVUXt3qEIAbKXsejxSAAAiAAAiDABFz9 qATKhYDuk9JBEKB5wSlP3SEvqhZl5amV3NqQql z22bNvks9ZxUhxpZ1Cz/1r3V79vPSfPQyBwi3fdu7s/zZNOdVcZQXsoK2pLbwxWD856tNLRFe3p3xwRaX5BZrP1Hc9pSrbTtNH5WIWWNdFUk2dkh6pu/w19Wj367adXCFNuC3dol6k0hvS2iEpllhzarirES5fD1uu/dUcBVIAACIFA2CdgKAf7lwUGDB9paJn6aWHdRpKsFQgR8dNhD1VvXSTgh4PSTxOzI7vEcp wiR8uO5rGcZjTzg1304HV UpsmeWh4ht BXfL5AGqT8iGNLvrezf1Ozk3XH8LBvnX6HOmcJ7epU4b/TrdCwM4OIQJ2Jvudr/j3t7 2FgNu7BLXVDxnLwDYDmFzu/Q8n7DhvlhzICgGuP1vV/OLHlFunVbFxULZfLzRahAAARBwJuC4IsCO3u5jJxT43tHP7IwodFAaKwL8E8aPTqxMs6eEt KQu2wv7WjfiPo30ZN5c/wYSsp6gm4pSq8QzqhG2ie 2TD/u7PnOUpThEH6Br8DcrpfrlV1bM5dHipC1BUN1XHaledkh64sdrzCTruyrewSzrpNb eVBSG45PrkNvdrn01ZA 6kyQuuCjSF29cnoxs9n7820H9umOIaEAABECirBByFQKSGCQHx4vYLiX KONwwQWkIgeVZn9Dms/XDWnFwExZQmakzYV5 b51WN8TZ6P4myrGbScdTCDjZcUNS8dAFt/foDc5hB51dTmENJ 78vdOqhF0/RPos4D4QAAEQSGQCMRMCbDSLAZ0Q0C39b1uxizJXF1KlGpdQ1qJadIWUI9Ax SCt3lrBx7GtN1wx4Q5//oAcOrC7f 5tx6nXjDzp/oM0KPV7Oib1TJM7fkF7Xv RkvIvoK7ZTalv0 A1XOfjt/sv5rDAok vpIeL/u2mc9WZs7ycLmbkPNOVwwNyubqZt/g nkLAjR0i54BzA aPnUHde99Om13kM jsEqsBbUeMptw5M2jfOSoW4uD7puX4Z/RCiIiwgBtmblcs3PQ7rgEBEACBskAgZkLAaUVAN NnZz7rreohQoCdvXDEPINf835ykaMunkwo7s9cXJFWFgkF7gSRZ8D3r//vpcWEhkhGPLVlD/WeVugrn5f9OXTAgqGhJARylx6iH/rUC2vZmJ1h9 mjAklqbhyoPHjUXvEl0IcFtF7oFTUp TXVzO7zOaUcuO3WjZxiyqX5QseeT0GG3io1WYw4oZrxYMa96XWi/4NJDLURYeYrQRBEAABEpCIGZCgBtltSLA37kVAvKuAeGYf5HaiJ4afKbYrgKdkJDvd/reSQhwm2cvLKRH 1/imjk7l GNplPanmDMWScE2Nk3TjsdklDIlejud3KYTo3T1S/uCSdHwI0dIvHx8d1H6N6Wi8lNgh 3ReesdfUJcSAnYtrZoiYwqoJr GvLHHc1OPHF9yAAAiBQlgjETAhEa0UgVAj4VwGO/6pxXIQAC4XsM00CYQI3HT2newNKHnUgZIbpFFsXSYY h6i530kIyNn/fK26ZS9cIaBuARTbHbsdts91uDHJv1Wxen9/ToCdE1ZZuhUCdiEVXT6AVY4Al M2bOGm38O5xoqv2GESTlm4FgRAAATCJRAzIcANidWKAC/VizyBcGb8JV0RWJG5n pOaOg6LCBvTZM7Rhfzt3J8YmubVcfGMzTgZIfOSfPfOqbUplWaMwycBI6uPKfkPjXmrytD3a4Z7kOE60EABECgLBOImRBwWhFgaKEx 2ByHicMijj/7p9q GL6nFQnX6/4qieD4nAMr3WwkFcT/vGpg/4FtfAmD/lH1037AfqXVRToBIQOS2XjOyJp169wLXWw3ZAS04FLrF7aluqdRi7TqfkJAdlM45Od3PbQpnhq062Xk5 j34IiGv53TnzH4u084O3cFAbpLx7Oxi4SPa3qDocCS7cwlUsaIKJ/6 i c9Gp//UkDgMYOx00fTfIeDj8ryg4 2gwAIgIAgEDMh4LQiwN9zBj47Xs7nr5BXha7vdYo ese/a4Adtby7gK9XDxeyul XLPhw0698uxL4w3WN2HA5VVoZulNBiAOxQ6He7y6ivLXf ZIFR1ZyHxaQT6qTh5p6ap3ViXxu7pcP3uE6apHz3nf5QCG Rz3RUA0puD1lz 5kQbVOpzKd7HI6qVDeNSBCLFaHFKl1ib6yOgkSrw0QAAEQKI8EYiYE3KwIlEegsAkEQAAEQAAEyhIBV0JAHCMcyX8jPVCoLEFEW0EABEAABECgrBJw/PVB/r2BSD8sAvijO1kw9e6dkRabMPetezVyNgljBBoCAiAAAiBgNAFbIcBkPEneA33ato0YEosAvn/b1m0Rl4EbQQAEQAAEQAAEYkPAUQgIMRBp9RABkZLDfSAAAiAAAiAQewKuhEDsm4EaQAAEQAAEQAAE4kEAQiAe1FEnCIAACIAACCQIAQiBBOkINAMEQAAEQAAE4kEAQiAe1FEnCIAACIAACCQIAQiBBOkINAMEQAAEQAAE4kEAQiAe1FEnCIAACIAACCQIAQiBBOkINAMEQAAEQAAE4kEAQiAe1FEnCIAACIAACCQIAQiBBOkINAMEQAAEQAAE4kEAQiAe1FEnCIAACIAACCQIAQiBBOkINAMEQAAEQAAE4kEAQiAe1FEnCIAACIAACCQIAUsh0KNnjwRpIpoBAuYRqFmzJj0z9xnzDIfFIAACpU7AUggMGTqEatSoWeoNQoUgAAJ AlMmTwYKEAABEIg5AYQGYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hKAEEjcvkHLQAAEQAAEQCDmBCAEYo4YFYAACIAACIBA4hJwLQSO5rSlOQdzKWtk7I05 fkAurbFItp3jmj8rMKI68zzZNM9nuOUXZBJl0hl1qJu9Hz WrrF484WLqeL5z0an/ S5T1ym63Kn5PmoZE5/jrDsYvLHvl0F0p 9/c0f0ewzR3arKItuT18f D qZW23ff/XP/ACS9T5l IUmgCrffa38idqTG7ihn2aVuHXtjmb6/V57xnKw1t0T5gJ3Oa/Eg2ZQ24kyYvuCpm7UPBwTGUKGOmvPTJpkke6pSROM izJWfyzurjKG3TntfttKnMjWjmR/sogevK51eEIy4Nt34k9 v8nuvdFpX/mtxJQR4sHT2PEdppTgw3Dhfp 7Z/Hgn2nvXRupZfQB1TKlNq4ocIjvkeTnuHKR4UPJSVgScrlovD1K78oVze3eHv04WJe1TTtCzLsQIPyDDM4Jt5X/3ydALGW5H996302ZJHAx/bRmtWpjihKpUvhf9Yfdy4b5ZcyAocIR4Ckc4lYox5bQSHl8LDu1OmDETL8wsrBunnY6aM Tyuk8fZfkOiZedXK94x9VI yTQ7/zcTcsJb8IUqQ3M5jdpnQITFq77g6rBMcjvtTYpH9Jor/8Z0N4/UajeP/IJYqTtLM/3OQoB4cRe2VE6g0LALumDozpFuRP5OzeOmG0f1rwvfdnkDFWuvtH1y1Etn21pnVY3sAohmDoNZt1LWXWUsl3HVo gtZfPCah4vvboDbF7YMJdJWIuY6ePpvkWwkQnOJnV8EbTKW2P xWcRHxg2Y5RnV6lYW9kxX11xm41hsd76wWfRmUmGO74SMR i1abYv0slqSduucumkLIaRyo7zT53S/eld/ OigM L2YviE4WSiJ7bjXT8BRCPAsbkNBIT0/tXJYy klBVzSB epbqnUYu067VK OoPXtVWIgKuXv0C77v9DWC9HufwGRUvdO5ODA1co8HbpeZZhD50QcrrvzfFjKCnrCZ/N0VhRsetDt2JKLkMO1ehCFeKhl1nx/fPGjaHbpj2RsA7UzVhXZzlu7inta5z6J5z2RDI wim/LF0b62expCzUiQqXZ7fyGE59bsaBWhf/1q/gmMTpDYTYbCaRuuDRKwFQLcCby0/FTnPiFLNyIezXGkrI ep50PXOOL6epiO2Jpl PW93rj1tvfKO4QRXxKLP8KJ8wzk37t/TGs3NONQ5bpdLFkkb/gNPOUB5rVYBBCZEzn0GV/N4NHLl 37CYvdemWya2 1z2woj3MY LwLyhrzr2 Pwkh0b1BT19eghzzE23adfqugLgT4mVlYReaXRSjF7E4Nca5Xsp1EOVeucEfB 3RL6jcVTHn5qUgxpZdHFDOteD6Vi46Gcgr4H8vX/S6b8x82foOKti2LiTXRCemdPkdn/Tw53NwO97efrmvfBHascq30I31dSveCOS7cL/Y2SW347ZRo6lg5vqQcJycByKeNdEXunYKESrySuS EeNGtJnLm7dqIz02I3T52o51OONDN87VvBY1b0fHc83Ymb5cGDHuxPuB3yFy EiNfYvv5HcXx8DV zkfRcTMVV52cWy7vnOzumnVXu4nq 9EncfO eP54hlU 0XX7/J7TDcjZ8byfer7VnyntqHbYX uEvO 7P1gTpRdzoEcOv3t7/5Cxy8OfYfIYVyryYKb9zKusSZgKQTk5C41Ts3F8QBod/f7lP95ki92Ix4oMctVHaAYMD2nB5WeGDDswGWnIZzSssIaNLIoSY9fzGKZWy1LXSpyWg2Q4 g6NHJb3DzEchlqSMJqaUuO 6ttsMphsFPCXO/iDQvpkRH 0uTYevoj/rgaz7Tf3H7El/jYf9fFNPPqOoG8CSH6RD6BYMAPM8fr5o dUSwPQvSHCGFc/32zQB/plvTdCAExtjhZtOK50DwOdUwViy12b0D5kx j11tuoJ91W0tVqgVFgrzKINsqz0ZuTAqNP/J3r9XbQWfn3OMLD31/eKY2xus01t2sQKmzInUMyP ur Ts6NopBEib3v6Xqiou1dwX9ZlyZF0UdnIzPqyeMRGDviEpNBnXLc9ndx hB5p968u1kd8PwtnLzl8OzYn sLpfnoiwgNHl Mg5QW76zi5Ep7ZXff/I70l1MiBsedIr4p59fRkNrNfMl PBzyI/t LfVnlCumRB1WmLsWE3ljgpe5S3DQ8tu4zq/n1vQMC6Wdllm 7f9hvKn5dNci6WbhKl xscfMkJWAoBeSagm8mo4kCeaQnHI8d15DiUKhpUM7jsp799nuq9ttoXG5ZfFPz/rNhFYovqaFWHJpftZulTjcu7GciiDqvy1Ze43H7VdquBXtKwgCoi5KVqNWdBLGX2fOEg7T2y3bdEJ3PRxRR1eRFyAhDbqROUVkNYvHyEGNCFWGSbuE13N3zXV9zYfaH5BGq9IoRy9UuhCWGys SkJM5NONDiI7p77JeWMXOd0FP5OMU0rZZmRRxUdTTy9Sxe1HZatYnHHQt1WRiKXSeycBOCSBZPKmsWk GMD7mfnVa2WLRavTvYMYv3w5Wf/ceXc8HCSOzqEe8HOeymiiC7 zmspgo3u3Hr1HdOYQG759pq9UokzgkWw/9fF2p17H7fjhzup80/daEWv13n62ennA 7vuA cxpLYvn riWX0cVH7w8kKvO9uveEbtIjkoNVMar mNZu5Cyd1n SlBKwTUpXM1vqkqZtFBQnWfnxya6S6 F45hn5IJL MUZR 6sgl1 fM63wtYnpXLL8Vr9vi3GdZp5Q832CVkuUk6U5e/5HY5Za3bla qbrvtWXZhAassZquwgPySl1 u6gOqvgz437 c8B21qprhe7DV/lZn4sLJC8ele3mIVQp5R4DqHNTtqdzXv8/wL3vykqOwXwjJI6fHBDKN7V4Qsn3s/DncJcIJwtmJZV/Rz7qXkO6x1zkJmY8QMFaJobqXvSzMxFK1EL78LD6WE9zaZfWylGfA3G55XDFL9Xv5GZNZWrEOd3wIdlZjQ3zvhic7t7fOE/1piT pUX0/qKttqnCyu1 MZbFzIlxHrYpqpxVFO5FhxUL0nRBsIpFbiCAxq3azEuUUb9cJBfUdZbWCqXtPqM 8upNCbo/uXWhVV/lxyfGxpJgQYPhyZrfuwVUHmHyNeMGqil6eBTstcbPiTZ3/Is0e1NxHRZ6VyysV6n59Hni6sw50wsUNbjcPklDNTspbvIydditYKXQ75a4TbvJSpM7RC1Hmm02lzKOCKukBNa8 bCoHnTCUt/RwgumQF78MvKjF7EDMSHVnUejyNuR2s7jkHAT 6OKNdis3opxFhTfT0qKzDFRxpsbu1ZUh3Xixmy0Jx 0UDrGaUYotokLs8pka/NHFrdXtfjoHIvcp5xXIgkwXanNiLcdtncaHzM7OsbrlyeJfhBh17wfZNjWmrBNO8thR3xVWwpzrdeo7Xl0Qz8q4YWfpmtatiw0ju3eh p3OFvl9ojpepzHsZpndaSzJqzHquSzqe0I1XtcW/qs NWnLt5t OaUAIhQkCn4HQPrqxy1fiZmAEJISA6jxNaxiwZR9c07UN7nwzdxy8vnaoKWgyGSbuq0VdvLKJfnghdbRAP6ghv0uLecauLbc/SxfvENi6n2ZraFlXt60SA1aqEW1FhpaLVl4DVDEpdirR68XH8kEUbLysn3/syJV9SSLXeSaWUVybQWmULGT/Qb9Z nngpdvDGS2m490yJrhJv VwEnnFzvO/nMyvS494Y7sInxvi2CzqFBbgOed yaq/60pXHJc a7Q58EgzOnAtugdU5HdHGl70Jk9kuttGpZejG s 9SZS8UsJJbjqRqtolhC4Lk0Fe5/GHPid8oTB5qVs4CE5i1AlQXZnyKoI66 pw2zdUL8lDfTf4n7Fe9UJXDNSwn1qn3fj448a7fcmnYkVEdT7yM6WGFHU8f 1dzZBnkeL9MOqFQ74w1i3fBt8P4vmWtz5bvV/E/ZwczM5V/rcsPOTVNHVlRe27Xn2a vqnyQuP0pFBF9EfP xBvBoqb31TRbf8LpSfGTe26AQN15074CLtQV5qyEnnHJ3GktWKh AkvyfUJFu1bFV0ye9ucX6AuqMIDj06BHxCQF0SF8ujYrlUVCVmTfKs3GqWImYUvAy 1OsQ7m25OJD8xSpSPs3KLtOcBwsny4jldDUTWvydHzCx5US0V7xIxGxK/F3enWB3OIU6y1SFgFP58qzT7WltdoJBF7rQZaELZmyv7pRD0X/qrg/mou6SEHWu3OFfjubDmfjFKDKVeWlW5sDtEZndwmY1uU0dusyJTx1clnskZFyotlmtBjktv1oxVftPzoSWk8HsHjX5GdGNdTmrX4RqdDNkeeeMyLZWM93V8Ws3VmRW6tiT7ebvcrxJucO8YkMOtVixtloNtBofugNg5PGpru644amudvH7QYwV9RnRjSG7 0Xb5PvkNsnPk7qqJGfKi2eJnxVZgKr5ImoZdpn6drZYTQDkusX4Uet0OkXQbixZrcTJIs7uhEKZra4d6rtF9wxFxxWaXYrjOQK6l7bTcbtmIy2Z9VYrCiUrNb53z/Fm8yePOhCVQ2riawlqBwEQAIHyRyBsIeA0 yp/iErfIvWEwNJvQfRq1MX o1c6SgIBEAABECgpAddCwGnJraQNwf1BAuougLLIxik7vCzahDaDAAiAQHkk4FoIlEfjYRMIgAAIgAAImE4AQsD0EQD7QQAEQAAEjCYAIWB098N4EAABEAAB0wlACJg AmA/CIAACICA0QQgBIzufhgPAiAAAiBgOgEIAdNHAOwHARAAARAwmgCEgNHdD NBAARAAARMJwAhYPoIgP0gAAIgAAJGE4AQMLr7YTwIgAAIgIDpBCAETB8BsB8EQAAEQMBoAhACRnc/jAcBEAABEDCdAISA6SMA9oMACIAACBhNAELA6O6H8SAAAiAAAqYTgBAwfQTAfhAAARAAAaMJQAgY3f0wHgRAAARAwHQCEAKmjwDYDwIgAAIgYDQBCAGjux/GgwAIgAAImE4AQsD0EQD7QQAEQAAEjCYAIWB098N4EAABEAAB0wlACJg AmA/CIAACICA0QQgBIzufhgPAiAAAiBgOgEIAdNHAOwHARAAARAwmgCEgNHdD NBAARAAARMJwAhYPoIgP0gAAIgAAJGE4AQMLr7YTwIgAAIgIDpBCAETB8BsB8EQAAEQMBoAhACRnc/jAcBEAABEDCdAISA6SMA9oMACIAACBhNAELA6O6H8SAAAiAAAqYTgBAwfQTAfhAAARAAAaMJQAgY3f0wHgRAAARAwHQCEAKmjwDYDwIgAAIgYDQBCAGjux/GgwAIgAAImE4AQsD0EQD7QQAEQAAEjCYAIWB098N4EAABEAAB0wlACJg AmA/CIAACICA0QQgBIzufhgPAiAAAiBgOgEIAdNHAOwHARAAARAwmgCEgNHdD NBAARAAARMJwAhYPoIgP0gAAIgAAJGE4AQMLr7YTwIgAAIgIDpBCAETB8BsB8EQAAEQMBoAhACxgHqZgAAAXZJREFURnc/jAcBEAABEDCdAISA6SMA9oMACIAACBhNAELA6O6H8SAAAiAAAqYTgBAwfQTAfhAAARAAAaMJQAgY3f0wHgRAAARAwHQCEAKmjwDYDwIgAAIgYDQBCAGjux/GgwAIgAAImE4AQsD0EQD7QQAEQAAEjCYAIWB098N4EAABEAAB0wlACJg AmA/CIAACICA0QQgBIzufhgPAiAAAiBgOgEIAdNHAOwHARAAARAwmgCEgNHdD NBAARAAARMJwAhYPoIgP0gAAIgAAJGE4AQMLr7YTwIgAAIgIDpBCAETB8BsB8EQAAEQMBoAhACRnc/jAcBEAABEDCdAISA6SMA9oMACIAACBhNAELA6O6H8SAAAiAAAqYTgBAwfQTAfhAAARAAAaMJQAgY3f0wHgRAAARAwHQCEAKmjwDYDwIgAAIgYDQBCAGjux/GgwAIgAAImE4AQsD0EQD7QQAEQAAEjCYAIWB098N4EAABEAAB0wn8f/4abES3u2YrAAAAAElFTkSuQmCC[/IMG]

---

### Post by doug-ravennasprings on 2024-10-13
apt-get update shows problems:

This line is displayed a couple dozen times
Get:12 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) oracular/universe arm64 Packages [15.5 MB]

Then this line...
Ign:12 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) oracular/universe arm64 Packages

The web proxy is showing successful access to [http://ports.ubuntu.com/ubuntu-ports/dists/oracular/universe/binary-arm64/Packages.xz](http://ports.ubuntu.com/ubuntu-ports/dists/oracular/universe/binary-arm64/Packages.xz)

Proxy is also showing 
sub="http" request="0xd775800" function="connect_server" file="dns.c"  line="1288" message="connect() on AF 10 socket to 2620:2d:4000:1::19  failed: Network is unreachable"

---

### Post by doug-ravennasprings on 2024-10-13
More errors updating this post.
I give up.

---

