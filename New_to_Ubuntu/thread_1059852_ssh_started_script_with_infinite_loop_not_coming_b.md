---
title: "ssh started script with infinite loop not coming back on command prompt"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by mayank.0809 on 2009-02-04
Hi,

One my script runs a for loop forever.. 

When I run this script on different machine using rsh is comes back to command prompt but not with ssh 

lx-chcnvt022:msrivast::04:15 AM:81$ rsh -l convrtfo lx-chcnvt001 /home/msrivast/testperl.pl &

[3] 10206

lx-chcnvt022:msrivast::04:15 AM:82$ ssh -l convrtfo lx-chcnvt001 /home/msrivast/testperl.pl &

[4] 10274

 

[3]+  Stopped                 rsh -l convrtfo lx-chcnvt001 /home/msrivast/testperl.pl

lx-chcnvt022:msrivast::04:16 AM:83$ Warning: No xauth data; using fake authentication data for X11 forwarding.

 
..doesn’t return to command promt

As you can see, this script is doing nothing just running a for loop

 

 

lx-chcnvt001:~::04:16 AM:13$ less /home/msrivast/testperl.pl

#!/tp/bin/perl

 

my $k = 0;

for ( my $i = 10; $i > 0; )

{

$k = $i;

}
 

Any idea? Please help me how can i make it to return on command prompt using ssh.

Thanks,
Mayan

---

### Post by Cypher on 2009-02-04
Nevermind, you wanted a for loop..didn't read it properly..:)

---

