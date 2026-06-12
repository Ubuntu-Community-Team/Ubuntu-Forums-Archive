---
title: "How do you gain permission to a local folder?"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by suomalainen on 2010-01-14
Ubunteros,

I'm using a Ubuntu Live CD to access the HDD in which lies my 8.04 LTS o/s.

Do to an unknown problem in being able to launch Ubuntu, I want to access this HDD and attempt to save my .evolution folder. However, each time I try to cut and paste this folder to a new location I'm not being allowed to do it.

I attached a screen shot of the message I get and maybe someone knows what I need to be doing.

Thank You.

---

### Post by SchizmWolf on 2010-01-14
You've tried "sudo mv"?

---

### Post by akand074 on 2010-01-14
well yeah to move it you can use what the guy above said, but if you want to use the explorer in full permission type this into the terminal (make sure to not close the terminal until your done what you need to do or the explorer will close too.

```
gksudo nautilus
```

---

### Post by suomalainen on 2010-01-14
SchizmWolf,

Thank You for responding! I'm not familiar with this command "sudo mv" what will it do for me? Most importantly, how does it work?

It may sound strange me asking this but I'm on my windows laptop right now. On my Ubuntu PC right now I'm coping files from one drive to another in order to make room for the Ubuntu files I need to copy over. So this is where your advice comes in as per coping or getting access to local files in order to copy them.

Obviously, I need to type the command into terminal but then does this give me for that session exclusive rights to all files, folders and drives???

EDIT: akand074, thanks for your input as well. I forgot all about that one. I don't want to come across as a trouble maker but isn't that command illeagle to state in public due to the potential harm it may cause? My apologies if I'm mistaken....

Thanks again for your help All!

---

### Post by halitech on 2010-01-14
sudo mv is normally used in conjunction with the path to the file you want to move and the new location the file will be moved to

ie. sudo mv /path/to/file /path/to/new/location

as far as gksudo nautilus goes, that is fine to tell people about, its how to log into the system as root that is against the forum rules.

---

### Post by gdonwallace on 2010-01-14
In a nutshell, the command **sudo** gives your current user "root user" abilities (permissions) without having to actual login or switch to root.

gksudo does the same thing, only launches some gui programs with root user abilities (permissions)

---

### Post by suomalainen on 2010-01-14
So then it's agreed, I can boot up my Ubuntu live cd, go to terminal and enter "gksudo nautilus" and I'll be able to roam into any HDD that is connected to my PC and Copy files wherever w/o limitation?

Right?

---

### Post by audiomick on 2010-01-14
you should be able to.

---

### Post by suomalainen on 2010-01-14
All,

I opened terminal and used "gksudo nautilus" command but when I tried to copy the folder I wanted to copy to it's new destination I got following error messages.

IS their anything else I can do???

Thank You!

---

### Post by chaanakya_chiraag on 2010-01-14
Is the path to the .evolution folder /home/username/.evolution?  It seems like you don't have the permissions to even read the .evolution folder, which you should be able to do if it is **your** .evolution folder.  Also, what exactly are you trying to save it for?

---

### Post by marshmallow1304 on 2010-01-14
I have noticed the same thing.  I am unable to copy certain hidden folders in my /home from a live environment, even as root.

---

### Post by audiomick on 2010-01-14
that's odd. If you really have started nautilus with "gksudo", as far as I know you should be able to do anything.

One thing occurs to me: a couple of years ago I wanted to do something, and had  a similar permission problem. I am pretty sure it was a similar situation, i.e. my old desktop which had a broken Ubuntu (probably 6.10, I think) on it, and some files I wanted to retrieve.

If I remember rightly, I solved it (didn't know about sudo nautilus at the time) by creating a new user in the live cd boot who had admin privileges, then changing user. Sorry if that is a bit vague, but it was at least 2 and half years ago, I think longer.

---

### Post by J V on 2010-01-14
> **suomalainen said:**
> I don't want to come across as a trouble maker but isn't that command illeagle to state in public due to the potential harm it may cause?Best. Quote. EVER!

But seriously, just run gksudo nautilus and it will pop open  a window you can copy in fine...

Edit, gksudo -u <yourusernamehere> nautilus :P

---

### Post by suomalainen on 2010-01-14
> that's odd. If you really have started nautilus with "gksudo", as far as I know you should be able to do anything.

Well this is not working for me. I started the Ubuntu Live CD then I navigaed to the HDD where my .evolution file is and then I right clicked "Copy" and then tried to paste it into another HDD and it would not work.

What can be done? Everyone makes this sound easy but it ain't working for me!

---

### Post by suomalainen on 2010-01-14
J.V.
> Edit, gksudo -u <yourusernamehere> nautilus 

What do I use as a user name if I'm booting from a live CD????

Thank You

---

### Post by audiomick on 2010-01-14
Ok, given what marshmallow1304	wrote, I am curious now.

I will boot my machine from a live CD, and try this out. As far as I know, what people have been telling you should work, but I do not disbelieve you.
Can you tell me which live CD you are using? I have a couple here, and if I can use the same one as you, I will.

---

### Post by suomalainen on 2010-01-14
I'm using the 8.04LTS 64 bit version live CD.

---

### Post by audiomick on 2010-01-14
ok, got that.
Sorry it took me a while, I missed your answer earlier.
I will try it now.

---

### Post by audiomick on 2010-01-14
ok back again. I have booted into a 32bit 8.04 live cd.
I was able to copy the folder .evolution from my home folder to another partition on the other HDD in my machine. I did the following.
open a terminal
application> accesories> terminal
type
```
gksu nautilus
```

in the file manager window that opened, click on the partition where my home folder is in the "places" field on the left.
select view> show hidden files
right click on .evolution

click on the partition I wanted to copy to.
once more, select "show hidden files"
select "paste" from the "edit" menu, or right click in the window and "paste"

I am going to boot back into my normal install now.

---

### Post by suomalainen on 2010-01-14
audiomick,

Thank you for taking time to explain in detail what you did with success. This clarifys things much better.

During the Interim, I tried to get my Ubuntu 8.04 back up and running. This time when I booted the entire startup went into some sort of FSCK mode and produced tons of questions to which I needed to answer "Yes" to.

Anyway, I got Ubuntu 8.04 up and running and hesitant to close it down now...

I followed your steps and was able to copy .evolution to another drive.

So if I understand correctly, if my machine don't boot up tomorrow morning then I can still use this ".evolution" folder to install my emails as if nothing ever happened. Is this correct?

Would you by and chance know if there is any sort of file or folder I can keep so that if I ever need to do a re-install then all the programs and modifications I've made with this o/s won't be lost?

Thank You again for Your support!

---

### Post by audiomick on 2010-01-14
Glad things are looking better.

As far as your settings go, nearly all of them are in your home folder. For that reason, I have, as is often recommended here in the forums, my home folder in it's own partition. If you have to re-install, you can just re-mount this partition without formatting, and things like .evolution just get found again by the application when you start it, as well as all your data being still there.

In your situation, if you re-install and then copy the saved .evolution into the place where it came from, i.e. the home folder in the new installation, evolution should start as if nothing had ever changed from the old installation.

There is an add on for firefox that will make a list of installed applications
[https://addons.mozilla.org/en-US/firefox/addon/13153/](https://addons.mozilla.org/en-US/firefox/addon/13153/)
there is a command also that I even saw in a thread today, but can't find. I will have a bit of a look and post a link here.

edit:still can't find the post with the command. :(

there is this
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by audiomick on 2010-01-15
Hallo again.
found what I was looking for, not a command actually.
Here
[http://ubuntuforums.org/showpost.php?p=8663531&postcount=5](http://ubuntuforums.org/showpost.php?p=8663531&postcount=5)

---

### Post by chaanakya_chiraag on 2010-01-15
The command would be
```
dpkg --get-selections > installed-software
```
To restore the list of installed software:
```
dpkg --set-selections < installed-software
```

---

### Post by ShawnB391 on 2010-01-19
How can i locate a folder on my hard drive from a live cd? Ubuntu has found my windows partition, but not my orignal ubuntu partition...

---

### Post by PenguinInside on 2010-01-19
> **ShawnB391 said:**
> How can i locate a folder on my hard drive from a live cd? Ubuntu has found my windows partition, but not my orignal ubuntu partition...

Could you run mount -l in the terminal (Applications: Accessories: Terminal) and paste the result here?

---

