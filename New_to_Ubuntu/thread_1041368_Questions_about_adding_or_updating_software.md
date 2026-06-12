---
title: "Questions about adding or updating software"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Drjim on 2009-01-16
Hi,

I'm used to the Windows approach to adding or updating software where I buy a CD or download a program and then install it. I have Openoffice 2.4 and wanted to upgrade to the new 3.0. I went to openoffice.org and downloaded the Linux vs of 3.0 but it's not clear where to go from there. I thought I might have installed it (it's now on my hard disc somewhere) but when I started Openoffice it was still vs 2.4. 

I know the preferred method is to go to "Applications" and choose "add/remove" and choose from a list offered. There were upgrades for Openoffice on the list which I used but still ended up with vs 2.4. 

1. Am I doing something wrong?
2. Is there a way to add/update programs by downloading them via my web browser and installing them? If so, is there a reason not to do it this way?

Thanks,

Jim

---

### Post by SteveDee on 2009-01-16
The easy way is go back to the OpenOffice site and download the .deb package.
Then you can double click on the .deb file which will auto run the GDebi Package Installer.

---

### Post by beastrace91 on 2009-01-16
To upgrade to open office 3.0 follow the step detailed [here](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml).

As for other software in the future, my apps provides repositories you can add (such as you do for Open Office 3.0 in the above link) this is the was way to add the programs this way when the repositories get updated a little message will appear in your icon tray telling you there are updates available.

Hope I helped some,
~Jeff

---

### Post by beastrace91 on 2009-01-16
> **SteveDee said:**
> The easy way is go back to the OpenOffice site and download the .deb package.
Then you can double click on the .deb file which will auto run the GDebi Package Installer.

I've actually found that can be a bit of a headache for OpenOffice... adding it to the repositories I feel is always the best bet when ever you can.

~Jeff

---

### Post by PriceChild on 2009-01-16
You are correct, with Ubuntu (and linux) you don't just buy a cd and pop it in normally.

Really, you shouldn't even install random things off of the internet that you find if you want to maintain stability.

Ubuntu uses "software repositories" and you can read more about the process here: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Do you really want OOo3? Or do you just want it because it is one more than 2? Remember that installing it yourself means you won't get automatic security updates and critical bug fixes from Ubuntu. Software from Ubuntu's software repositories is also reviewed and touched up by many developers to ensure it works perfectly with the rest of your system. If you're sure that you want to risk it, then googling "open office 3 ubuntu" got me to several guides on installing it. I still wouldn't. OOo3 should be in Jaunty I believe but not completely sure.

---

### Post by beastrace91 on 2009-01-16
OpenOffice 3 provides a much better "feel" than open office 2.x does... especially if you are coming from using MS Office, the UI is much more similar. And I have never had any issues with Open Office 3 on, Ubuntu or Windows...

~Jeff

---

### Post by SteveDee on 2009-01-16
> **beastrace91 said:**
> I've actually found that can be a bit of a headache for OpenOffice... adding it to the repositories I feel is always the best bet when ever you can.

~Jeff

Jeff you are probably right. OpenOffice is quite a complicated app.

---

### Post by Joeb454 on 2009-01-16
> **PriceChild said:**
> Do you really want OOo3? Or do you just want it because it is one more than 2? Remember that installing it yourself means you won't get automatic security updates and critical bug fixes from Ubuntu.

Actually I found a PPA on Launchpad, it's proved to be quite good so far. I found it from a softpedia article.

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

While I realise PPA's aren't official, I haven't yet had any problems with this one :) There's been a few updates to it as well

---

### Post by PriceChild on 2009-01-16
> **Joeb454 said:**
> Actually I found a PPA on Launchpad, it's proved to be quite good so far. I found it from a softpedia article.

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

While I realise PPA's aren't official, I haven't yet had any problems with this one :) There's been a few updates to it as well

Yep I think that ppa might be a good one, but be careful with them and applying updates. History has taught some of us why you shouldn't blindly add repositories.

> 1232136431 0116T200711 [msg(ubottu)] wfm
1232136432 0116T200712 [ubottu(n=supybot@ubuntu/bot/ubottu )] Common Sense: Just because you can, does not mean you should (and especially recommend to 
          others). Think before you do. "Works for me" does not mean it is ok. The latest version of everything is not always useful if you aim for 
          stability. Please see [http://geekosophical.net/random/worksforme/](http://geekosophical.net/random/worksforme/)

---

### Post by beastrace91 on 2009-01-16
> **Joeb454 said:**
> 
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Thats the same link I posted above ;)

~Jeff

---

### Post by Joeb454 on 2009-01-16
> **PriceChild said:**
> ahem

I know, I know.

However, the OP wants to upgrade to OOo 3.0 and that link is the exact same guide I followed to update it on my system. As far as I've noticed it does do it all properly (removes 2.x) as well.

Though you're right, WFM posts are pretty useless, and mine was very borderline :)

---

### Post by mapes12 on 2009-01-16
If your browser is Firefox it will have saved a file on your Desktop called 00o_3.0.0_LinuxIntel_install_en-US-deb.tar.gz

You need to double click it to start the Archive Manager to unpack and install it. I've assumed you have downloaded the US English, Linux DEB version.

---

