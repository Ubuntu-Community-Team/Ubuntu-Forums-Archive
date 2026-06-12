---
title: "Getting Wireless working on new install while offline"
date: 2015-02-11
forum: Networking &amp; Wireless
---

### Post by GraphiteFingers on 2015-02-11
I in a catch-22 situation.  I'm away from home in a hotel room with only WiFi [no RJ45 to plug into].  I brought a LUbuntu [14.10] installation disk and figured I would use this opportunity to get my laptop setup.  It never occurred to me that the hotel room with be void of a wired connection!

I'm here with my wife, and have occasional access to my wife's Win 8 laptop so I can use it's wireless connection to download files, so I acquired the following, and transferred then to my laptop using a USB Flash Drive:


[LIST]
[*]dkms_2.2.0.3-1.1buntu_all.deb 
[*]gksu_2.0.2-6ubuntu2_amd64.deb 
[*]libgksu2-0_2.0.13~pre1-6ubuntu4_amd64.deb 
[*]ndisgtk_0.8.5-1ubuntu1_amd64.deb 
[*]ndiswrapper-common_1.59-2_all.deb 
[*]ndiswrapper-dkms_1.59-2_all.deb 
[*]ndiswrapper-utils-1.9_1.59-2_amf64.deb 
[/LIST]

When I attempted to install them, I soon discovered that I needed gcc to compile them, which is absent from my Linux installation.  Then I discovered that without the ability to use apt-get to acquire all the files needed to build and install gcc ['cuz my laptop has no internet connection], the task is a veritable nightmare of dependency upon dependency!!!

Does anyone have an idea of how I can to this?  I looked for a gcc binary, but found none.  Is there, perhaps, a friendly [apt-get-ish] way to use Win8 to collect the required gcc source files so I can move them over to my Linux laptop?  Or is there a place that I can acquire a tar of ALL the files needed to build gcc?

---

### Post by chili555 on 2015-02-11
>  the task is a veritable nightmare of dependency upon dependency!!!Your forefathers, those old grey-bearded Linux nerds that came before you, thoughtfully named this 'dependency hell.'

This describes a way to get ndiswrapper from the install DVD or USB. Post back if you get stuck; I shall be nearby grooming my beard!

[http://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568](http://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568)

---

