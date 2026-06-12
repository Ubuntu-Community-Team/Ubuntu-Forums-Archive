---
title: "Windows Print Driver Share in Linux"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by kublah on 2008-06-03
I have mainly 3 printers to worry about, HP 4350s, 4240,s and 4250s.

What I am aiming for is to setup that print driver repository so that when a new printer is shared to a windows machine (from the linux print server) , the windows machine will automatically select the available print driver from the linux server and install it!(take a breath)
   (this is what i understand the [print$] subconfig is for, please correct me if I am wrong)

So far I have not found any documentation on the subject even in the samba help. All it simply says is the [print$] is where windows will look for a driver. 

I setup the folder as /var/libs/samba/printers with the windows drivers kind of just dumpped in there. As I understand it, I need to setup some sort of packages for windows to grab? -- Right now it is just the pure dump of config files that I use while on a windows machine to setup these printers. 


[print$]
      comment = Printer Drivers
      path = /var/libs/samba/printers
      browseable = yes
      read only = yes
      guest ok = yes      

Please help, if you know of any documentation I would appreciate it very much!!!

---

### Post by Nausser on 2009-02-24
I too am battling this very same obstacle. I'm hashing it out with my printers here at home so I can do this to my ubuntu servers at work and ultimately use ipp and have this auto driver install work even then.

Let me know if you have been able to resolve any of this.

I have been trying to follow the instructions here:

[http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/classicalprinting.html#id2619652](http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/classicalprinting.html#id2619652)

-Nausser

---

### Post by Yorkie125 on 2009-02-25
I'm also looking into this same issue!

I have found some articles that may help...

[http://www.swerdna.net.au/linhowtosambaprint_1.html](http://www.swerdna.net.au/linhowtosambaprint_1.html)
[http://wiki.samba.org/index.php?title=Samba_as_a_print_server&printable=yes](http://wiki.samba.org/index.php?title=Samba_as_a_print_server&printable=yes)

I will look into it further tomorrow...

---

### Post by Yorkie125 on 2009-02-26
I've not managed to find an clear instructions.

I'm stuck on Running rpcclient with adddriver

>  The following command and its output has been edited for readability: 

root# rpcclient -Uroot%xxxx -c 'adddriver "Windows NT x86" \
  "dm9110:HDNIS01_de.DLL: \
  Hddm91c1_de.ppd:HDNIS01U_de.DLL:HDNIS01U_de.HLP:   \
  NULL:RAW:Hddm91c1_de.DLL,Hddm91c1_de.INI,          \
  Hddm91c1_de.dat,Hddm91c1_de.def,Hddm91c1_de.hre,   \
  Hddm91c1_de.vnd,Hddm91c1_de.hlp,Hddm91c1KMMin.DLL, \
  HDNIS01Aux.dll,HDNIS01_de.NTF,                     \
  Hddm91c1_de_reg.HLP' SAMBA-CUPS

I am struggling to adapt that for our printer driver.

Why are some of the files in the example above seperated by colons and some by commas? How do I know what to do with my files? what does that "NULL:RAW" do and why is it in that list of files?

---

