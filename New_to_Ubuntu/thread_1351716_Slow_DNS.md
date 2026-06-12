---
title: "Slow DNS"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by Scott O'Nanski on 2009-12-10
Every time Ubuntu comes out with a new build it seems something happens that causes it to resolve DNS poorly. This time, with 9.10, there's no difference.

Does anyone know how to fix this?

I've searched, googled etc. Found nothing I understand...

Thanks.

---

### Post by sandyd on 2009-12-10
Use OpenDNS?

---

### Post by x33a on 2009-12-10
Try changing the dns.

here are a few good tools to help you find the best dns server.

[http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)

[http://www.grc.com/dns/benchmark.htm](http://www.grc.com/dns/benchmark.htm)

---

### Post by lovinglinux on 2009-12-10
See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

Also see [http://blog.taragana.com/index.php/archive/simple-firefox-hacks-to-boost-performance/](http://blog.taragana.com/index.php/archive/simple-firefox-hacks-to-boost-performance/)

If that doesn't help, try another DNS server like OpenDNS or Google DNS as already suggested.

---

### Post by Scott O'Nanski on 2009-12-10
It doesn't happen in Jaunty, or in Windows. I've had this problem before with other builds but they keep changing the applications with each build so I don't know how to fix it.

It's something inherent with Karmic.

---

### Post by lovinglinux on 2009-12-10
> **Scott O'Nanski said:**
> It doesn't happen in Jaunty, or in Windows. I've had this problem before with other builds but they keep changing the applications with each build so I don't know how to fix it.

It's something inherent with Karmic.

I forgot to mention to update your system. There were some dns related package updates a couple of days ago that fixed some DNS issues.

---

### Post by Geoff918 on 2009-12-10
Sometimes I'll use the following DNS servers:

[http://www.comodo.com/secure-dns/](http://www.comodo.com/secure-dns/)

Those servers absolutely fly. I have Comcast as my ISP, and sometimes their DNS servers crawl. At my ex-g/fs place her DNS servers are worse. So I've pretty much hard coded those DNS addresses into my internet setup.

Are you experiencing any type of packet loss? The problem may be before the DNS server is even reached.

---

### Post by VanCardboardbox on 2009-12-10
I experienced what I took to be slow DNS action after installing 9.10 on both my main box and a laptop, waiting several seconds for addresses to be found. Disabling IPv6 corrected the problem on both machines.

---

### Post by k3lt01 on 2009-12-10
Give [this]("http://ubuntuforums.org/showpost.php?p=3996845&postcount=5") a go.

---

### Post by Scott O'Nanski on 2009-12-12
Can't figure it out. I'll just revert back to Jaunty.

Karmic is a bit of a fail imho.

---

### Post by mcdjork on 2009-12-12
There's a glitch in Karmic having to do with ipv6. The problem is over my head, but I've been able to work around the problem though.

All you have to do is add a line to your grub menu entry that disables ipv6. Hopefully the issue is resolved for Lucid, because I understand that ipv6 will actually be important in the not so distant future.

This is what you have to do:

sudo gedit /etc/default/grub

change the line that says:

GRUB_CMDLINE_LINUX=""

to:

GRUB_CMDLINE_LINUX="ipv6.disable=1"

Then you have to run the grub2 setup to actually build the new menu:

sudo update-grub2

Just restart your computer, and your browsing should be snappy!

---

### Post by SkyNet2029 on 2009-12-12
it sounds like your router does not handle ipv6 correctly. This is pretty common problem. Just disable the ipv6 in firefox or change your nameserver in the /etc/resolv.conf file. the only prob is that the /etc/resolv.conf gets overwritten with every new dhcp lease.

---

### Post by EndPerform on 2009-12-17
> **SkyNet2029 said:**
> it sounds like your router does not handle ipv6 correctly. This is pretty common problem. Just disable the ipv6 in firefox or change your nameserver in the /etc/resolv.conf file. the only prob is that the /etc/resolv.conf gets overwritten with every new dhcp lease.

I've been having the same problems as the OP, however, I cannot change the nameservers since I'm in a work environment.  I've disabled IPv6 everywhere I can think of (kernel, Firefox, etc) and have went as far as installing nscd to try to cache DNS entries, and even that isn't working.  I know it's not the network, because hooking up my Macbook to the same connect works fine 100% of the time.  Older versions of Ubuntu work fine, as do the various other Linux distributions in use here.

---

