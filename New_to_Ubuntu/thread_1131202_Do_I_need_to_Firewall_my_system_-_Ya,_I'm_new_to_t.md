---
title: "Do I need to Firewall my system? - Ya, I'm new to this"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by Irish1 on 2009-04-20
First I just wanted to thank everyone who replied to my last post.  I'm going to stick with Ubuntu now that I understand a little better its inner-workings.  I have been told that I do not need an anti-virus or a spyware program because there are only like 6 viruses for Ubuntu, but just to be safe wouldn't it be a good idea?  In terms of a firewall I would want to keep people from gaining access to my computer. Is there a way to firewall Ubuntu?

On a side note, is there an application to play store-bought DVDs anywhere?  I keep getting a copy-right protected message.  Don't get me wrong here, I just want to watch them, not start my own business.

Thanks for any help,

Colm.

---

### Post by steve101101 on 2009-04-20
ubuntu has a firewall by default based on iptables.

---

### Post by steve101101 on 2009-04-20
you need libcssdvd 2

Installing libdvdcss2

First you need to install the libdvdread3 package using the following command

sudo apt-get install libdvdread3

Now download the libdvdcss2 library using the following command

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

For Ubuntu 6.10 (Edgy Eft) users use the following command

sudo /usr/share/doc/libdvdread3/install-css.sh

If you want to download libdvdcss2 library manually you can download from here

---

### Post by coldReactive on 2009-04-20
> **steve101101 said:**
> you need libcssdvd 2

And to get that...

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by steve101101 on 2009-04-20
> **coldReactive said:**
> And to get that...

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

+1 yeah forgot about that for a second. brain fart.

---

### Post by Irish1 on 2009-04-20
Thank you sooo much, this has worked like a charm.  Everything is going very smooth. I'm sticking with Ubuntu for sure.

Thanks again everyone for the help, it's much appreciated.

---

### Post by ugm6hr on 2009-04-20
Re: firewall.

If you do need to configure the firewall, use ufw (or gufw) for simplicity.

To enable:

```
sudo ufw enable
```

---

### Post by steve101101 on 2009-04-20
you can also use the gui firestarter which i find useful at times

---

### Post by steve101101 on 2009-04-20
> **Irish1 said:**
> Thank you sooo much, this has worked like a charm.  Everything is going very smooth. I'm sticking with Ubuntu for sure.

Thanks again everyone for the help, it's much appreciated.

and im glad your sticking with ubuntu. you will find its very nice to have an os that is able to be completely customised. i love ubuntu.

---

### Post by rolando on 2009-04-20
I use these

**_Firewall_**
Mobloquer (download from the repos) can block IPs you dont want

**_Netstat_**
Open a terminal and type this in 

watch -n 2 netstat | grep tcp

(press Ctrl C when you want to exit)

Wait a couple of minutes and all the active TCP connections to your machine will show. I like to look at mine every now and then and compare against what I have going on (dropbox, Firefox, skype, pidgin etc etc).  also might show up some odd ones as well, never know.

---

### Post by steve101101 on 2009-04-20
the default firewall, iptables, which is there by default i believe is very secure and strong. Also linux itself has very little viruses/trogans compared to other oses (Win/Mac)

---

