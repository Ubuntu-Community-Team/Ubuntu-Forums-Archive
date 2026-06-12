---
title: "Program install"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by carnelian on 2010-02-25
I have always fought shy of Linux, but I have recently come around to it, and have installed Ubuntu 9.10 on one laptop, and have done a partition of XP and Ubuntu 9.10 on another.  Being an absolute novice, I am quite pleased with myself and both went on without any problems. I have now installed some of the available programs included in the download, but I would like a couple not in this package.  The Linux language frightens me to death, and I don't know what it all means.  Can anyone tell me, in non-Linux language, how to get thes two programs installed?

---

### Post by PRC09 on 2010-02-25
What are the programs you are trying to install?

---

### Post by gallifrey on 2010-02-25
Can you be more specific about the programs you want to install?? I have recently moved to Linux, but have become fairly adept at finding .deb packages for programs not in the Package Manager! :D

---

### Post by carnelian on 2010-02-25
Java Runtime and Thunderbird

---

### Post by BrandonBan6 on 2010-02-25
> **carnelian said:**
> Java Runtime and Thunderbird

Nothing scary about the Linux language, you just need to get to know it a little better :) Java and Thunderbird are great apps to start with... 

Open terminal. To do this, click your Applications menu > Click accessories > click terminal. Now type or copy and paste the code below:

```
sudo apt-get install ubuntu-restricted-extras
```

This will install java, along with a handful of other codecs and things you may end up needing. For a complete list of things this command lists, review this page: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

There seems to be some issue with the mozilla site from my end, so I'm not sure the format the installer downloads in. I'll let someone else chime in here.

---

### Post by 2hot6ft2 on 2010-02-25
For thunderbird while you have the terminal open you can either just add thunderbird to the end of the command in the post above like this
```
sudo apt-get install ubuntu-restricted-extras thunderbird
```
 or use
```
sudo apt-get install thunderbird
```

---

### Post by snowpine on 2010-02-25
To install Thunderbird,

```
sudo apt-get install thunderbird
```

You can also use the Ubuntu Software Center if you aren't a fan of the terminal. :)

As a new user, I strongly recommend installing applications from the official Ubuntu "repositories" (using apt-get or the Software Center) rather than downloading random stuff from the internet (like you might be used to from Windows). This is the best way to make sure you use software that is tested and trusted. Good luck and welcome to the forums!

---

### Post by PRC09 on 2010-02-25
Why not just use the Software Center..To install Java go to Applications > Ubuntu Software Center > in the search box enter Ubuntu Restricted Extras and click install.This will install java flash and support for most multi-media stuff such as mp3 etc...
Do the same for Thunderbird.. Thunderbird will then appear in Applications > Internet. Hope this helps...

---

### Post by carnelian on 2010-02-25
It says (sudo) password for ..........
Tried to type my password, but it does not accept any typing

---

### Post by snowpine on 2010-02-25
> **carnelian said:**
> It says (sudo) password for ..........
Tried to type my password, but it does not accept any typing

Your password won't be shown on the screen while you're typing it. :)

---

### Post by carnelian on 2010-02-25
It says (sudo) password for ..........
Tried to type my password, but it does not accept any typing

---

### Post by gallifrey on 2010-02-25
If you want the LATEST version of Thunderbird, the best way, IMO, is to get it from the Ubuntuzilla repository (just google Ubuntuzilla).

---

### Post by snowpine on 2010-02-25
> **gallifrey said:**
> If you want the LATEST version of Thunderbird, the best way, IMO, is to get it from the Ubuntuzilla repository (just google Ubuntuzilla).

Curious why you are recommending unsupported 3rd party software sources to a new user, instead of the tested and trusted applications in the Ubuntu repositories? :(

---

### Post by carnelian on 2010-02-25
Will have to go back and read all this, but going back a few posts I have done as suggested.  Still frightened me to death - lines and lines appearing.  The end result is that I now have Thunderbird up and running, but when I went to do the "thinkbroadband speed test"  it still said I needed Java.  Where is it - do I have to do anything - it certainly downloaded dozens of lines when I copied and pasted.

---

### Post by PRC09 on 2010-02-25
For java you can use the software center and in the search window enter sun-java and select the sun-java 6 plugin and install and see what happens.You should close and re-open your browser if it was open during install....

---

