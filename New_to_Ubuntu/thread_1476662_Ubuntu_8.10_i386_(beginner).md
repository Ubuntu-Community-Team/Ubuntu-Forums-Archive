---
title: "Ubuntu 8.10 i386 (beginner)"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by bonzer1990 on 2010-05-08
[SIZE=2][FONT=Verdana]Hello there,
I have an amd athlon processor [2.8 GHz,x64 - black edition 7850+],
ubuntu v 8.10 i386 in a CD,my questions regarding it are

1)I have tried it both;as a standalone application in windows to check it and even installed it removing windows xp,so now How do I install it completely as a separate OS without removing windows 7 (my current OS) in the same partition or possibly a different partition??

2)Secondly,when i installed it using boot from disc,it installed correctly but none of the audio or video files played,so can you guide me on how to download and install the necessary drivers for system,audio,video,networking etc??

3)Can you give me some links to download free software for linux?

Do kindly answer my queries.
Thank you.
[/FONT][/SIZE]

---

### Post by lisati on 2010-05-08
1. Have a look here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
2. Have a look here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
3. Once you've installed Ubuntu, have a look at the Applications->Ubuntu Software Center

---

### Post by sadaruwan12 on 2010-05-08
> **bonzer1990 said:**
> [SIZE=2][FONT=Verdana]Hello there,
I have an amd athlon processor [2.8 GHz,x64 - black edition 7850+],
ubuntu v 8.10 i386 in a CD,my questions regarding it are

1)I have tried it both;as a standalone application in windows to check it and even installed it removing windows xp,so now How do I install it completely as a separate OS without removing windows 7 (my current OS) in the same partition or possibly a different partition??

2)Secondly,when i installed it using boot from disc,it installed correctly but none of the audio or video files played,so can you guide me on how to download and install the necessary drivers for system,audio,video,networking etc??

3)Can you give me some links to download free software for linux?

Do kindly answer my queries.
Thank you.
[/FONT][/SIZE]

For your firs question refer theses two links they'll help you to understand how to do it.

[http://lifehacker.com/5403100/.........harmony]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")

[https://help.ubuntu.com/..../WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

You could install medibuntu repository which contains most of the restricted media codec's and softwares. Use the below command to add the repository to your sources open the terminal and copy paste the command and press enter.list to do this you need to have be connected to the Internet.

code:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

For free software you don't need to go any where it's right there in your Synaptic Package Manager just go to System -> Administration -> Synaptic Package Manager.

If you need special softwares you could use this site to look them up.

[getdeb]("http://www.getdeb.net/welcome/")

And get a copy of the new version of the Ubuntu os it's now 10.04 and known as Lucid Lynx down load it from [http://www.ubuntu.com/getubuntu]("http://www.ubuntu.com/getubuntu"). Because you're using very out dated version.

---

### Post by NightwishFan on 2010-05-08
Ubuntu 8.10 is out of date. I would get a new version here: [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

More software than most would need is integrated right in the Ubuntu Software Center. Free to download and install, and automatic updates/fixes to everything.

---

