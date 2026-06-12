---
title: "Installing Downloads"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by rawbertb on 2011-06-07
Okay--I am beginning to get REALLY pissed off.  I have downloaded several programs (Adobe Reader, Firefox 4, and finally Windows 7), and they have all disappeared into etherland.  How do I install downloads?  I am getting REALLY frustrated!

---

### Post by wolfen69 on 2011-06-08
> **rawbertb said:**
> Okay--I am beginning to get REALLY pissed off.  I have downloaded several programs (Adobe Reader, Firefox 4, and finally Windows 7), and they have all disappeared into etherland.  How do I install downloads?  I am getting REALLY frustrated!

What are you using? Ubuntu 11.04 comes with Firefox 4. You're downloading windows? Adobe reader (the .deb) is [here]("ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.4.2/enu/"). Normally, downloads go to /home/user/Downloads. You're leaving me kind of confused, especially the windows part.

---

### Post by rawbertb on 2011-06-08
I downloaded Windows 7 from Microsoft because I am totally frustrated with Ubuntu.  I have no idea which Ubuntu I have, but I think it is 10 something.  Everything I have tried to download goes to Archive Manager, and I cannot install anything.  What am I doing wrong?

---

### Post by wolfen69 on 2011-06-08
I'm not sure what you mean by "Everything I have tried to download goes to Archive Manager". Archive manager is an app, not a place downloads go to.

Btw, sorry ubuntu is frustrating you, but it's not for everyone. Just like windows isn't for everyone.

---

### Post by kostkon on 2011-06-08
Use the software center to install your software (Adobe Reader included). And [here is a good tutorial on how to install software in Ubuntu]("http://psychocats.net/ubuntu/installingsoftware").

Hope that helps.

---

### Post by nzjethro on 2011-06-08
What kind of "downloads" do you mean? Like the .deb packages? They should go to the Downloads folder in your home folder. You can access that folder by clicking on Places > Downloads. It may be that you are saving them to somewhere else though. Does it ask you where you want to save the files?

---

### Post by Random_Dude on 2011-06-08
> **rawbertb said:**
> I downloaded Windows 7 from Microsoft because I am totally frustrated with Ubuntu.  I have no idea which Ubuntu I have, but I think it is 10 something.  Everything I have tried to download goes to Archive Manager, and I cannot install anything.  What am I doing wrong?

When you download, you probably have the option "open with" selected, instead of save file. Is that it?

---

### Post by Paqman on 2011-06-08
Ubuntu comes pre-installed with a perfectly good reader for PDF files, so you don't need to worry about that one. For anything else, you should be able to get what you need from Ubuntu Software Centre. Downloading installers from random websites is the dodgy Windows way of getting software, on Linux we have it much easier than that.

Having said that, if you're on an older version of Ubuntu that doesn't come with Firefox 4 then you'll need to add the Firefox 4 PPA to get it:

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```

Once you do that run Update Manager and it will upgrade you to Firefox 4.

As for downloading Windows 7, is that even possible? If you've downloaded it from anybody other than Microsoft _do not install it_. Installing software or operating systems from an untrusted source is a bad idea.

---

### Post by Mark Phelps on 2011-06-08
> **rawbertb said:**
> Okay--I am beginning to get REALLY pissed off.  I have downloaded several programs (Adobe Reader, Firefox 4, and finally Windows 7), and they have all disappeared into etherland.  How do I install downloads?  I am getting REALLY frustrated!

My guess is that you're downloading Windows versions -- especially if you're just clicking a "Download" button displayed on a website.  Those download and nearly always Window apps -- and will not work with Ubuntu.

Others have provided suggestions as to how you SHOULD be obtaining apps for Ubuntu -- and NOT by downloading from websites.

---

