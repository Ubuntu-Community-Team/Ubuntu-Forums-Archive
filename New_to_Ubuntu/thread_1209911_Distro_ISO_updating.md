---
title: "Distro ISO updating"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by paul_h on 2009-07-10
Is the current Ubuntu distribution !SO constantly updated or is left unchanged? In other words, is the 9.04 ISO downloaded in April 2009 the same as one downloaded in July 2009, or does the later one include all updates to that date?

Paul.

---

### Post by halitech on 2009-07-10
unless they release a 9.04.1 download then it would be the same no matter if you downloaded it on the first day 9.04 was available or 3 months later.

---

### Post by trot2millah on 2009-07-10
It stays the same, and then once you first use the distribution roughly 200+ updates will be available to get you up to do date.  But the ISO itself doesn't get updated, only every 6 months for distribution releases.

---

### Post by note32 on 2009-07-10
its gonna be the same then when you install it you use the update manager to update the ubuntu;)

---

### Post by kandieyman on 2009-07-10
To get at the real core of your question, there is no way to save yourself from a considerable amount of waiting for updates when you have to reformat Ubuntu after making a mistake. We have all suffered through it many, many times. Sorry...

---

### Post by paul_h on 2009-07-11
Thanks for the responses.

In September I plan to help a group of somewhat dissatisfied MS Windows users install Ubuntu (dual-booting) with the hope of convincing them that Ubuntu is an attractive alternative to their current systems.

The initial installation of Ubuntu from CD is slick and creates a good first impression, but what I was hoping to avoid was each person having to do a massive download to update their newly installed distro.

I wonder whether there would be any way to download all current updates for the distro then install them on a DVD to be used to update multiple newly installed Ubuntu systems. Dreaming maybe, but never say "never".

Any suggestions welcome.

Paul.

---

### Post by Elfy on 2009-07-11
Assuming that you have one fully updated machine either copy /var/cache/apt/archives or you can use aptoncd. 

Personally I had issues with aptoncd not working - but I think it was me rather than the software - I now just backup my archive and copy it over.

---

### Post by paul_h on 2009-07-11
> **forestpixie said:**
> Assuming that you have one fully updated machine either copy /var/cache/apt/archives or you can use aptoncd. 

Thanks forestpixie. This is probably the clue I'm after. I've installed APTonCD, had a quick look at some on-line documentation and willo run it soon. I hope it works for me. Much appreciated!

Paul.

---

### Post by Bradtek on 2009-07-11
8.04 LTS version has had 8.04.1 & 8.04.2 (and did I read somewhere 8.04.3 ?) 

> **paul_h said:**
> I was hoping to avoid was each person having to do a massive download to update their newly installed distro.

They would be doing that if they installed windows 

> **paul_h said:**
> 
I wonder whether there would be any way to download all current updates for the distro then install them on a DVD to be used to update multiple newly installed Ubuntu systems.


As mentioned already aptoncd

If you use aptoncd you will still need to have downloaded/applied them on 1 pc  and have to apply all the updates but in your software sources Add the CD Rom that you made and it should get them from there before Internet.

Alternatively you can do 1 install yourself, download all updates, customize your software / apps etc then use remastersys t make an installable Live CD of your up to date customized Ubuntu

[http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com)

---

### Post by kandieyman on 2009-07-11
Making your own Live CD is likely the most difficult option, but it is want you will want to do. AptOnCD is a bit hokey (it does not let you save every package you will want), and it only saves you the package download time, not the install time, which can also be significant. You really want to create your own install.

---

