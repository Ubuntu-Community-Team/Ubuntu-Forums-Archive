---
title: "Installation issues."
date: 2010-11-08
forum: New to Ubuntu
---

### Post by Shenachie on 2010-11-08
I downloaded the 10.10 iso ifle and it checked out as per the lubuntu wiki. 

I boot from it and I get asked if I want English, then if I want to install, and then the screen goes a grey colour, there is no sign of activity from the disc drive (no green light flashing) and I am left wondering if anything at all is happening. 

I am trying to install it to a Pentium 4 processor running at 3.2, and with I know for sure 256 ram but some checks are suggesting 1 gig of ram so it should be more than capable of running Lubuntu?

Thoughts please?

Shen

---

### Post by A.Zan on 2010-11-08
> **Shenachie said:**
> I downloaded the 10.10 iso ifle and it checked out as per the lubuntu wiki. 

I boot from it and I get asked if I want English, then if I want to install, and then the screen goes a grey colour, there is no sign of activity from the disc drive (no green light flashing) and I am left wondering if anything at all is happening. 

I am trying to install it to a Pentium 4 processor running at 3.2, and with I know for sure 256 ram but some checks are suggesting 1 gig of ram so it should be more than capable of running Lubuntu?

Thoughts please?

Shen

How are you trying to run the setup ?
Did you burn the iso on a cd ?

---

### Post by coffeecat on 2010-11-08
> **Shenachie said:**
> with I know for sure 256 ram but some checks are suggesting 1 gig of ram

Which checks are they? It would be an idea to find out for sure because 256MB RAM is not enough to run the live CD.

Have a look in the BIOS. That will tell you.

---

### Post by Shenachie on 2010-11-08
Yes burnt to CD.

Shen

---

### Post by Shenachie on 2010-11-08
256 is not enough? Thier home site is suggesting 128 is fine? hence I thought I was good. 

Right off to pull the CD and play with the bios. Back in five. 

Right. Can't get into the bios as it is going to the Debian grub. Then getting so far and sticking. 

BTW I don't want the live CD to run I want to instal a version of Linux on this machine so I can use it... and so far am being frustrated at every turn. Debian wouldn't recognise my WiFi so I began trying lighter and lighter versions. Slitz runs but again won't connect to the wifi. 

Shen

---

### Post by coffeecat on 2010-11-08
> **Shenachie said:**
> 256 is not enough? Thier home site is suggesting 128 is fine? hence I thought I was good. 

My bad. I misread your post and the title tag. [SIZE=5]L[/SIZE]ubuntu. I need new glasses. :-#

---

### Post by Shenachie on 2010-11-08
Managed to get into the Bios (delete key) and yes it is 1 gig of ram which is why I cannot understand all this hassle over installing. At a gig I would have thought Ubuntu would install but it wont. Lubuntu surely should?

Shen

---

### Post by sikander3786 on 2010-11-08
Checking the integrity of the downloaded image will be an option. It might be cause due to a corrupt image or a bad burn.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

You need to compare it to the relavent one from these.

```
7fb4b82a7faadb209e2ae4ca831283e5  lubuntu-lucid-20091220.iso
693535024d729984c0093c220b4c8405  lubuntu-lucid-20091222.iso
f0a8c7875931d244d4d866a3ee3bf802  lubuntu-lucid-alpha1.iso
e487fcf7833d04e6944fc58458346c50  lubuntu-lucid-alpha2.iso
e6d92c714bee7d85214486d9eef3482a  lubuntu-lucid-20100215.iso
548b29279999975429cb8c966a13b9da  lubuntu-lucid-alpha3.iso
616ff7ba77672d14ffb3b1a3e1524618  lubuntu-lucid-beta1.iso
1bfcb7bf3616dea4614c056023fe482b  lubuntu-lucid-beta2.iso
b328dabc1438db32ad0e90d88dfc9c43  lubuntu-lucid-beta3.iso
386a227968cbabc89e1a23b95035160e  lubuntu-10.04.iso
306660d3cce4844117414dfe62095c82  lubuntu-maverick-alpha1.iso
f9417ba2f6e36b86e909d2d25173f8f0  lubuntu-maverick-alpha2.iso
aaa7f31fd712cd7376859594849d4806  lubuntu-maverick-alpha3.iso
f3437c33044cf2398ca255de13bf8f86  lubuntu-maverick-beta1.iso
f0bf7e2e2fbcb58d8fabe4a8453249bd  lubuntu-maverick-beta2.iso
098254aeb0153b10bcfce948c43a0df6  lubuntu-10.10.iso
```

Also check the disc for defects.

1GB RAM should be enough to run either Ubuntu or Lubuntu. What problems were encountered with Ubuntu?

---

