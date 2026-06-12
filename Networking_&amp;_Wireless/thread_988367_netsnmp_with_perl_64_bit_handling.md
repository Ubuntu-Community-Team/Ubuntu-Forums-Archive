---
title: "netsnmp with perl 64 bit handling"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by tripaam on 2008-11-20
Hi,

I have one perl script which uses to get the ifInOctets and ifOutOctets. The return values are in longer than 32 bit value. like terabytes. How can the perl script handle that. It is not returning 0. But when i used snmpwalk -v 1 -c public localhost | grep Octet I am getting proper value like below in Olive color.

IF-MIB::ifInOctets.1 = Counter32: 10224560
IF-MIB::ifInOctets.2 = Counter32: 32958883
**[COLOR="Olive"]IF-MIB::ifInOctets.3 = Counter32: 1120513328970[/COLOR]**
IF-MIB::ifOutOctets.1 = Counter32: 10226345
IF-MIB::ifOutOctets.2 = Counter32: 573815822
IF-MIB::ifOutOctets.3 = Counter32: 396

let me know is it fixed in which version and how can i get it?

#!/usr/bin/perl

# interface.pl

use Net::SNMP;
use RRDs;

$oid_ifNumber    = "1.3.6.1.2.1.2.1";
$oid_ifDescr     = "1.3.6.1.2.1.2.2.1.2";
$oid_ifInOctets  = "1.3.6.1.2.1.2.2.1.10";
$oid_ifOutOctets = "1.3.6.1.2.1.2.2.1.16";

$database_eth0 = "/var/www/rrd/databases/eth0.rrd";
$database_eth1 = "/var/www/rrd/databases/eth1.rrd";
$database_xyxs0 = "/var/www/rrd/databases/xyxs0.rrd";

   my ($session, $error) = Net::SNMP->session(
      -hostname  => shift || 'localhost',
      -community => shift || 'public',
      -port      => shift || 161
   );

   if (!defined($session)) {
      printf("ERROR: %s.\n", $error);
      exit 1;
   }


my $numInts = $session->get_request($oid_ifNumber. ".0");

for $i (1..$numInts->{$oid_ifNumber.".0"})
{

    $name = $session->get_request($oid_ifDescr . ".".$i );

    if ( $name->{$oid_ifDescr.".".$i} eq "xxxx" )
    {
        $in = $session->get_request($oid_ifInOctets . "." . $i);
        $in_bytes = $in->{$oid_ifInOctets.".".$i};
        $out = $session->get_request($oid_ifOutOctets . "." . $i);
        $out_bytes = $out->{$oid_ifOutOctets.".".$i};
        printf("Interface in ::%lld\n",$in->{'.1.3.6.1.2.1.2.2.1.10.3'});
        printf("Interface out::%lld\n",$out_bytes);

    }
}

die $session->{ErrorStr} if ($session->{ErrorStr});


br,
APT

---

