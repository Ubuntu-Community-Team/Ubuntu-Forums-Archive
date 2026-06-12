---
title: "New to Linux &amp; Kubuntu, Fritz!Card question"
date: 2005-07-29
forum: Networking &amp; Wireless
---

### Post by kiwi_bloke on 2005-07-29
I've been using Windows 98SE since it came out, saw no reason to move to Windows ME and even less reason to change to XP . . . read about Linux in a PC mag and have installed Kubuntu 5.04 (dual boot)on my AMD Athlon PC after checking various Live CDs from Suse, Knoppix, Kantonix ... in the past 2 weeks. I have learnt to mount my C: and D: fat32 partitions thanks to the helpful Forum/Wiki documentation. 

To the point.  I would like to install my AVM Fritz!Card DSL. I installed in under Windows but that experience doesn't help me here. I have spent the last 2 days reading postings in the Wiki, Support Forum and googling but have yet to find a clear set of steps for Kubuntu 5.04 in one place. The more I read, the more confusing I find the matter despite the obvious time and effort given by helpful people.

Can someone please help me, a newcomer to Linux and Kubuntu, setup my my Fritzcard?

---

### Post by tdjokic on 2005-07-29
Do you still have your Kanotix? It has integrated suport for Fritz Card: [http://kanotix.com/files/kanotix/](http://kanotix.com/files/kanotix/)

---

### Post by kiwi_bloke on 2005-07-30
[QUOTE=tdjokic]Do you still have your Kanotix? It has integrated suport for Fritz Card: [http://kanotix.com/files/kanotix/](http://kanotix.com/files/kanotix/)[/QUOTE]
 Thanks for the tip, Tdjokic, but I prefer to stay with Kubuntu if I at all can - I like what it represents and what it has to offer. 

In fact I looked at the script Kanotix uses to install Fritzcard support but I don't understand the short forms (vocabulary/syntax?) nor their significance.

---

### Post by tdjokic on 2005-07-30
[QUOTE=kiwi_bloke] I prefer to stay with Kubuntu[/quote] This is OK, but many people have 2 or more Linuxes, nothing wrong with that.
> In fact I looked at the script Kanotix uses to install Fritzcard Kanotix scripts are extremly simple. You go to terminal as root and type (or Copy&Paste) [COLOR=Blue]the name of your script[/COLOR], from usr/local/bin and that's all. I dont have Fritz!Card and did only this for you:

root@box:/home/tdj# [COLOR=Blue]detect-fc.bash[/COLOR]
Error: No FRITZ!Card detected!

I am sure, you can try it from Live CD too.

---

### Post by kiwi_bloke on 2005-07-30
You're right. I had my Fritzcard up and running from the Kanotix Live-CD (which I stiil have).

Do I understand your point correctly? Do you mean that I can execute the Kanotix script in Kubuntu in order to set up my Fritzcard?

By the way, I read somewhere that I needed the following files:
isdnactivecards_3.3.0.20040728-2_i386.deb
isdnutils-base_3.3.0.20040728-2_i386.deb
libcapi20-3_3.3.0.20040728-2_i386.deb
libcapi20-dev_3.3.0.20040728-2_i386.deb
pppdcapiplugin_3.3.0.20040728-2_i386.deb
fcpci-suse93-3.11-07.tar.gz
so I downloaded them but don't know what to do with them.

---

### Post by tdjokic on 2005-07-30
"Do you mean that I can execute the Kanotix script in Kubuntu in order to set up my Fritzcard?" No, i dobut this very much. I have in mind that you can have Kubuntu & Kanotix installed on hdd, and use one or other.

---

### Post by kiwi_bloke on 2005-07-30
Thanks for the advice and help. :)

For the moment I can still use Windows for my DSL access so there is no real point in installing Kanotix/Knoppix too.

I'd still like to switch to Kubuntu tho' and set up my Fritzcard in Kubuntu so I'll be patient and see if I can work out how to do it or if someone can show me how to ...

---

### Post by wgth on 2005-08-05
Your 5.04 should have all drivers you need for AVM devices.
I somehow managed to get my AVm DSL SL USB device to work  under ubuntu by copying files from my (Kanotix based) old installation around.
Sorry, I forgot the details.
Important files:
/etc/ppp/peers/<provider definition file>
/etc/ppp/pap-secrets (login details)
/etc/ppp/chap-secrets (login details)
/usr/lib/isdn/ (firmware for your device)
/etc/isdn/capi.conf
/etc/drdsl/adsl.conf
Perhaps some entries in /etc/hotplug, and ...

"capiinit start" and "pon <pppd provider file name>" should do the job.

Sorry that I cannot help in more detail: perhaps, you should have a look at what Kanotix is doing when adding your device.

Good luck, Wolfgang

---

### Post by kiwi_bloke on 2005-08-07
Thanks for your post, Wolfgang.

In the meantime I found exactly what I was looking for. In case anyone else has the same challenge, look at this link, [http://www.ubuntu-de.org/viewtopic.php?t=1477](http://www.ubuntu-de.org/viewtopic.php?t=1477) , go down and read the Howto by *softbrain *, then skip the next post down to *Carsten*'s post which is the same thing but shorter. The posts are in German however.

---

### Post by wgth on 2005-08-08
Many thanks for the link.

---

