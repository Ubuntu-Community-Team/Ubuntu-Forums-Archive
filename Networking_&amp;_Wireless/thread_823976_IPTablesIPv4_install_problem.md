---
title: "IPTables::IPv4 install problem"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by neilneil2000 on 2008-06-09
I am trying to install IPTables::IPv4 in order to use linblock.pl

I am getting the following output

```

IPv4.xs: In function âXS_IPTables__IPv4__Table_set_policyâ:
IPv4.xs:329: warning: dereferencing type-punned pointer will break strict-aliasing rules
IPv4.xs: In function âXS_IPTables__IPv4__Table_get_referencesâ:
IPv4.xs:379: warning: pointer targets in passing argument 1 of âiptc_get_referencesâ differ in signedness
packer.c: In function âipt_do_packâ:
packer.c:407: warning: dereferencing type-punned pointer will break strict-aliasing rules
In file included from libip4tc.c:116:
libiptc.c: In function âiptc_initâ:
libiptc.c:312: warning: pointer targets in passing argument 5 of âgetsockoptâ differ in signedness
libip4tc.c: In function âis_sameâ:
libip4tc.c:226: warning: passing argument 1 of âipt_get_targetâ discards qualifiers from pointer target type
libip4tc.c:227: warning: passing argument 1 of âipt_get_targetâ discards qualifiers from pointer target type
In file included from libip6tc.c:111:
libiptc.c: In function âip6tc_initâ:
libiptc.c:312: warning: pointer targets in passing argument 5 of âgetsockoptâ differ in signedness
libip6tc.c: In function âis_sameâ:
libip6tc.c:258: warning: passing argument 1 of âip6t_get_targetâ discards qualifiers from pointer target type
libip6tc.c:259: warning: passing argument 1 of âip6t_get_targetâ discards qualifiers from pointer target type
ar: creating libiptc.a
IPv6.xs: In function âXS_IPTables__IPv6__Table_set_policyâ:
IPv6.xs:330: warning: dereferencing type-punned pointer will break strict-aliasing rules
IPv6.xs: In function âXS_IPTables__IPv6__Table_get_referencesâ:
IPv6.xs:380: warning: pointer targets in passing argument 1 of âip6tc_get_referencesâ differ in signedness
packer.c: In function âipt_do_packâ:
packer.c:407: warning: dereferencing type-punned pointer will break strict-aliasing rules
ipt_pl_DNAT.c:11:41: error: linux/netfilter_ipv4/ip_nat.h: No such file or directory
ipt_pl_DNAT.c:20: warning: âstruct ip_nat_rangeâ declared inside parameter list
ipt_pl_DNAT.c:20: warning: its scope is only this definition or declaration, which is probably not what you want
ipt_pl_DNAT.c: In function âparse_nat_rangeâ:
ipt_pl_DNAT.c:32: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:32: error: âIP_NAT_RANGE_PROTO_SPECIFIEDâ undeclared (first use in this function)
ipt_pl_DNAT.c:32: error: (Each undeclared identifier is reported only once
ipt_pl_DNAT.c:32: error: for each function it appears in.)
ipt_pl_DNAT.c:42: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:42: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:50: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:53: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:58: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:58: error: âIP_NAT_RANGE_MAP_IPSâ undeclared (first use in this function)
ipt_pl_DNAT.c:63: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:67: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:67: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:71: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:79: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c: In function âparse_fieldâ:
ipt_pl_DNAT.c:110: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:112: error: invalid application of âsizeofâ to incomplete type âstruct ip_nat_rangeâ
ipt_pl_DNAT.c:115: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:115: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:116: error: invalid application of âsizeofâ to incomplete type âstruct ip_nat_rangeâ
ipt_pl_DNAT.c:119: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:125: warning: passing argument 2 of âparse_nat_rangeâ from incompatible pointer type
ipt_pl_DNAT.c:132: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:145: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:152: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c: At top level:
ipt_pl_DNAT.c:160: warning: âstruct ip_nat_rangeâ declared inside parameter list
ipt_pl_DNAT.c: In function âstring_from_nat_rangeâ:
ipt_pl_DNAT.c:164: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:164: error: âIP_NAT_RANGE_MAP_IPSâ undeclared (first use in this function)
ipt_pl_DNAT.c:166: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:167: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:167: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:170: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:176: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:176: error: âIP_NAT_RANGE_PROTO_SPECIFIEDâ undeclared (first use in this function)
ipt_pl_DNAT.c:177: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:178: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:178: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:179: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c: In function âget_fieldsâ:
ipt_pl_DNAT.c:203: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:208: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:209: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:212: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c:213: error: dereferencing pointer to incomplete type
ipt_pl_DNAT.c: At top level:
ipt_pl_DNAT.c:230: error: invalid application of âsizeofâ to incomplete type âstruct ip_nat_multi_rangeâ
ipt_pl_DNAT.c:231: error: invalid application of âsizeofâ to incomplete type âstruct ip_nat_multi_rangeâ
make[1]: *** [ipt_pl_DNAT.o] Error 1
make: *** [pure_all] Error 2

```

Does anyone have any ideas?

I am running Hardy Heron on an atom x86 chipset

---

### Post by Rocket2DMn on 2008-06-09
Since nobody has suggested anything for this thread, I will pass this link on to you - [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo) and flag this thread for help.  Hopefully somebody on the Unanswered Posts team knows a little more than I do about this.

---

