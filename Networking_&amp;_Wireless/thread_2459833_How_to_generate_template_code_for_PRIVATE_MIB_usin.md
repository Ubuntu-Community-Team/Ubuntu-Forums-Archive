---
title: "How to generate template code for PRIVATE MIB using mib2c"
date: 2021-03-27
forum: Networking &amp; Wireless
---

### Post by hrisikeshsahu on 2021-03-27
My objective is to add a private MIB file -

1) I installed net-snmp-5.9 for Ubuntu 20.10
./configure --with-perl-modules
make
make install
2)I copied my private MIB file to /usr/share /snmp/mibs
Also set the env
 
#env MIB=ALL

The below example works –
mib2c -c mib2c.scalar.conf ucdDemoPublic

---> it gives output
outputting to ucdDemoPublic.c and ucdDemoPublic.h ...
depth: 1
Number of Lines Created:
2 ucdDemoPublic.c
1 ucdDemoPublic.h
3 total
Done.

but for the private mib –
#mib2c -c mib2c.scalar.conf product

there are errors –

[
You didn't give mib2c a valid OID to start with. IE, I could not find any information about the mib node "product". This could be caused because you supplied an incorrectly node, or by the MIB that you're trying to generate code from isn't loaded. To make sure your mib is loaded, run mib2c using this as an example:
   mib2c -c mib2c.scalar.conf product
You might wish to start by reading the MIB loading tutorial at:
[http://www.net-snmp.org/tutorial-5/commands/mib-options.html](http://www.net-snmp.org/tutorial-5/commands/mib-options.html)
And making sure you can get snmptranslate to display information about your MIB node. Once snmptranslate works, then come back and try mib2c again.
]


PLEASE GUIDE ME WHAT IS THE FURTHER STEP FOR ADDING MY PRIVATE MIB FILE....

THANK IN ADVANCE..

---

### Post by hrisikeshsahu on 2021-03-29
Hi All,
Please let me know if you are looking more information to this query.

---

