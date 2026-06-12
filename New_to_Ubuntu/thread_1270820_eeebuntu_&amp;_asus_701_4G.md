---
title: "eeebuntu &amp; asus 701 4G"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by jrev on 2009-09-20
Hi all,
I have an asus 701 4G netbook with eeebuntu.
The hard Disk is full and I cannot update my system.
I bought a 8 GB SD card to add up some memory.

my questions :

1)  Is it normal that eeebuntu fills up my 4G HD ? (I have no data of my own in the documents folder) 

2)  Can this SD card help me to work normally on this netbook ?

Thanks for your good answers :P

---

### Post by mikeyphi on 2009-09-20
> **jrev said:**
> Hi all,
I have an asus 701 4G netbook with eeebuntu.
The hard Disk is full and I cannot update my system.
I bought a 8 GB SD card to add up some memory.

my questions :

1)  Is it normal that eeebuntu fills up my 4G HD ? (I have no data of my own in the documents folder) 

2)  Can this SD card help me to work normally on this netbook ?

Thanks for your good answers :P

Yes to both - but...

On my Desktop the OS, alone, uses 6.79GB
On my asus 701 I use the 4G storage as '/' only - this uses about 3.3GB; I then use an SD card for my /home partition.

I'm also using the software changes required for Ubuntu from here:
[http://www.array.org/ubuntu/index.html](http://www.array.org/ubuntu/index.html)

You should consider reinstalling OS with separate '/' and '/ home' partitions.

---

### Post by jrev on 2009-09-20
I could probably re-install ubuntu with LXDE which is by far the lightest Desktop :P

---

### Post by t0p on 2009-09-20
I've got Eeebuntu on a 701 with 4GB SSD.  Similarly to mikeyphi, I've got / mounted on the SSD and /home on a 4GB SD card, which I have permanently in the card reader slot.  I suggest you do something similar.  Note: if you install Eeebuntu, you do not need to do any of the stuff detailed on the [array.org]("http://www.array.org/ubuntu/index.html") page linked to by mikeyphi.  Eeebuntu already includes those modifications.

---

### Post by Old_Grey_Wolf on 2009-09-20
The eeebuntu OS will use about 3 GB. Are you using Evolution or Thunderbird for email, and have a lot of email saved? Did you install a lot of applications, games, etc.?

You can move your /home to the SD card. That will also help if you do a clean install or an upgrade goes badly.

The 701/4G was one of, if not, the first netbooks. It was never intended to be a substitute for a laptop/notebook.

---

### Post by t0p on 2009-09-20
> **Old_Gray_Wolf said:**
> .
The 701/4G was one of, if not, the first netbooks. It was never intended to be a substitute for a laptop/notebook.

While I daresay you're right concerning Asus' intentions re the 701, it certainly *can* be used as a laptop substitute.  I use mine just about everyday, for all manner of computing tasks.  It is certainly *not* a glorified web browser, as some folk try to characterize it.

---

### Post by jrev on 2009-09-20
> **Old_Gray_Wolf said:**
> The eeebuntu OS will use about 3 GB. Are you using Evolution or Thunderbird for email, and have a lot of email saved? Did you install a lot of applications, games, etc.?

You can move your /home to the SD card. That will also help if you do a clean install or an upgrade goes badly.

The 701/4G was one of, if not, the first netbooks. It was never intended to be a substitute for a laptop/notebook.

I am not using Evolution or thunderbird for my mail (I uninstall them )
I am using Gmail & Firefox only !
I always use a fresh install through CD or DVD, formating all partitions

---

### Post by Old_Grey_Wolf on 2009-09-20
OK, then move /home to the SD card.

---

### Post by Old_Grey_Wolf on 2009-09-20
> **t0p said:**
> While I daresay you're right concerning Asus' intentions re the 701, it certainly *can* be used as a laptop substitute.  I use mine just about everyday, for all manner of computing tasks.  It is certainly *not* a glorified web browser, as some folk try to characterize it.

I agree, it can be used like a laptop; however, you have to do some modifications to the system; like moving /home to an SD card, adding an external CD/DVD drive, and so fourth. Also knowing the limitations of a single core processor with 512 MB of RAM.:)

My wife uses her 701/4G exclusively. She has no laptop or desktop at home. She is also a CPA and does her accounting spreadsheets on eeebuntu.

---

### Post by jrev on 2009-09-21
Thanks Wolf !

> **mikeyphi said:**
> Yes to both - but...
You should consider reinstalling OS with separate '/' and '/ home' partitions.

Cannot we use the SD card (8GB) for / and the 4G for /home ?
That would suit me better :)

---

### Post by t0p on 2009-09-21
> **jrev said:**
> Cannot we use the SD card (8GB) for / and the 4G for /home ?
That would suit me better :)

I was thinking of doing that.  Never tried it though.  But I think you'll be better off putting /home on the SD card.  I've got Eeebuntu on a 701 with 4GB SSD and 4GB SD card.  I've got / on the SSD, and it doesn't fill up completely.  Whereas /home fills 4GB all the time and I have to keep transferring stuff over to an external HDD.

So, my advice is to stick / on the 4GB SSD and use the 8GB SD card for your /home.  If you're anything like typical, you'll very likely fill it in no time.

---

### Post by jrev on 2009-09-21
I just started the installation with (/) on the SD card ...
We must be daring sometimes :guitar:

and finger crossed !

I will let you know ...

---

### Post by t0p on 2009-09-21
> **jrev said:**
> I just started the installation with (/) on the SD card ...
We must be daring sometimes :guitar:

and finger crossed !

I will let you know ...

Cool good luck.

---

### Post by jrev on 2009-09-21
Well,

the updating was great and the reboot ... not exactly what I wanted.
Never saw the Desktop again 
That is a pity. Why ? Something should be done about it.

In the meantime I will follow your method :P

---

### Post by jrev on 2009-09-22
When I start my 701 4G now, there is no boot anymore.

the connected CD Drive is flashing for sometime then stops and I am left with a black screen with a flashing white "-" on the top left side.

My battery charger went off as well,

What can I do now ? :confused:

Can I copy my install CD to an USB stick ?  Yes I can...

---

### Post by jrev on 2009-09-22
Now my Asus refuse to boot from the special Samsung DVD reader fed through 2 USB plugs.

I entered the BIOS and changed the Boot priority from "Hard Disk Drives" to "USB:USB2.0 CardRea"
to no avail

---

### Post by LewRockwell on 2009-09-22
> **jrev said:**
> Now my Asus refuse to boot from the special Samsung DVD reader fed through 2 USB plugs.

I entered the BIOS and changed the Boot priority from "Hard Disk Drives" to "USB:USB2.0 CardRea"
to no avail

what are your choices for boot priority?

you might try booting from a thumb drive instead of the internal card reader

are you able to select "F12" on power-up to get the manual boot device menu?

when you get it figured out we would recommend / on the 4GB and /home on the 8GB card(obviously)

.

---

### Post by jrev on 2009-09-22
Thanks Lew,

I think I am saved by the new feature of the ubuntu 9.04 :

"create an installation memory stick". The USB boot was OK

I am busy preparing the partitioning ...

But the installation was interrupted by a black screen, the net-book went off.

I will re-charge the batteries to-night and start again to-morrow morning

---

### Post by jrev on 2009-09-22
Can we put /usr on the second partition (the SD card) instead of /home ?

We can reduce /home to nearly 000 but not /usr which seems to be the biggest folder in  Ubuntu (2GB) :P

I did it and rebooted well then updated the eeebuntu version when rebooting again everything stopped.

Next try I will split ( / ) and ( /home ) only on different partitions

---

### Post by jrev on 2009-09-27
It would be interesting to know which line to add to the /etc/fstab file in order to mount the folder registered on the SD card :P

---

### Post by jrev on 2009-10-19
In fact the asus 701 4G can only receive a light version of Ubuntu for example the eeebuntu netbook remix

---

### Post by t0p on 2009-10-19
> **jrev said:**
> In fact the asus 701 4G can only receive a light version of Ubuntu for example the eeebuntu netbook remix

This is inaccurate. Before my current Eeebuntu install I had vanilla Intrepid with array.org working on my 701. I prefer Eeebuntu because of its hardware compatibility, not some mythical inability of the 701 to handle a full linux distro.

---

### Post by winotree on 2009-10-19
I only saw this thread this morning for the first time -- and I want to echo what **t0p** has said.  I, too, use my EeePC 701 for everything and have had Eeebuntu [and just about everything else] completely and securely installed on my 4GB SSD. Then I delete those programs that I'll never need, want or use, such as Evolution or Thunderbird because I can access Gmail with one click; Skype, Scim and Pidgin because I don't know anyone who uses them, and the various foreign-language font packages because I can't read or speak them* and will still have approximately 1.2 GB free space for my personal use*.*  

That said:  I want to wish you the very best success in what you're attempting.  :)

[Comments made regarding use of Eeebuntu Base 3.0 during July-September 2009]

Current stats using Xubuntu 9.04 [for example]

winotree@h1n1:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.5G  1.6G  1.8G  46% /

EDIT - as an afterthought [correct me if wrong] isn't NBR larger than Eeebuntu?

---

