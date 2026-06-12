---
title: "Guru help please!- 100% CPU constantly"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by daikon on 2010-02-03
Hi there

I'm new to all this, so please be gently. I know there are a few other threads similar to this but I can't seem to find my answer that way.

So- Just installed Xubuntu 9.10 after trying a few different installations of ubuntu, kubuntu SUSE etc. figured my system can't cope with KDE or, maybe GNOME so decided to try Xubuntu.

Installed fine, seems to be going swimmingly, then after installing a few things I use regularly, 100% CPU all the time, sometimes fails to boot.

Confused. Reinstalled Xubuntu, all fine, then installed things one by one- IBus and Anthy for Japanese support, ok. restart, CPU normal. Opera, flash plug in- restart, ok CPU normal. Mnemosyne, flash card system. again ok. Skype- installed but didn't start yet. Listened to BBC iplayer radio via opera. Next time I restarted- 100% constant CPU usage.
 System monitor says this:
Xubuntu karmic 9.10 (didn't install updates after 2nd installation-figured maybe there was a problem there)
Kernel linux 2.6.31-14-generic
GNOME 2.28.1

Memory 495.8 MiB
Intel(R) Pentium(R) 4 cpu 2.80GHz
available disk space 62.0 Gib

did Top command in Terminal: 
system monitor uses 45%cpu
dbus-daemon39%
gvfs-gdu-volume6%
gvfs-gphoto2-vo 6%
gvfsd3%


gvfsd is using 13%mem
opera is using 18%mem

Anybody any idea what its all about? all help appreciated!

Cheers
Matt

---

### Post by audiomick on 2010-02-03
Hi Matt.
I am not going to be able to help you to the end of this, but:
Let us know what your CPU is.
I can only assume it is fairly slow. My system monitor is only using around 4%
My dbus deamon is sleeping, but that doesn't tell me much, because I don't know what it does.
My CPU is a dual core @3.13GHz ( or there abouts.)

---

### Post by daikon on 2010-02-03
Hi, thanks for the answer

cpu is

Intel(R) Pentium(R) 4 cpu 2.80GHz

Do I need more info than this?
If so it'll have to wait a few hours, as I'm at work now, so I can't check anything till later.

Cheers
Matt

---

### Post by ubunterooster on 2010-02-03
@2.8 ghz your sys. monitor shouldn't use that much. (mine is now at 1ghz) It shouldn't even show up in xubuntu b/c sys. monitor is gnome. I reccomend you Kill system monitor.

---

### Post by daikon on 2010-02-03
> **ubunterooster said:**
> @2.8 ghz your sys. monitor shouldn't use that much. (mine is now at 1ghz) It shouldn't even show up in xubuntu b/c sys. monitor is gnome


Yeah I was wondering about this- apologies for being a bit slow, I only started trying to figure out linux in the past couple of weeks, so the Gnome/GTK/KDE Xubuntu/ubuntu/debian relationships are a little unclear to me.

Do you think I could have unwittingly downloaded some GNOME stuff as dependencies for skype/mnemosyne/ibus-anthy/opera?

or system files left over from previous distros I tried-ubuntu/linuxmint/opensuse?

Thanks for the reply
Matt

---

### Post by admiralspark on 2010-02-03
His CPU isn't the problem, I don't think. 
The only thing I can think of to check is this. Please open a Terminal and type the following:
> dmesg > mydmesg.txtThen copy the contents of that text file (located in your /home directory) into [this]("http://pastebin.com/"), and give us the web address it gives you back here. That file contains the system messages since Ubuntu started, which may help us figure out what's going on. 

Please, [COLOR=Red]***do not post the text file directly to this site.** *[/COLOR][COLOR=Black]It's usually quite large.

EDIT: 
[/COLOR]> Xubuntu karmic 9.10 (didn't install updates after 2nd installation-figured maybe there was a problem there)
Kernel linux 2.6.31-14-generic
**GNOME 2.28.1**

That should read XFCE unless I'm mistaken, not Gnome.

---

### Post by daikon on 2010-02-03
> **admiralspark said:**
> His CPU isn't the problem, I don't think. 
The only thing I can think of to check is this. Please open a Terminal and type the following:
Then copy the contents of that text file (located in your /home directory) into [this]("http://pastebin.com/"), and give us the web address it gives you back here. That file contains the system messages since Ubuntu started, which may help us figure out what's going on. 

Please, [COLOR=Red]***do not post the text file directly to this site.** *[/COLOR][COLOR=Black]It's usually quite large.

EDIT: 
[/COLOR]

That should read XFCE unless I'm mistaken, not Gnome.

hmm, maybe this is the source of my problem- its definitely booting up with xubuntu graphics and so on, but it said (I'm pretty sure) ubuntu and gnome in the system monitor. Maybe my installation has gone awry due to previous distros left on the system?

Thanks a lot for the reply, I'll try what you suggest when I get home tonight. Cheers
Matt

---

### Post by Sir Jasper on 2010-02-03
Hi,

I have Xubuntu 9.04 and I use gnome-system-monitor occasionally because I like its simplicity, but I do not leave it running because it is a high resource user.

If you would like to try CPU Graph then right-click on a blank area of the panel where you want it to show, scroll down a few lines to locate it, then click add. If you then click on the graph for details of resource usage you should find that, unlike system-monitor, it itself uses hardly any resources. After loading the details if you cursor to the top of the display box, then right click and hold down, then its display box it will freeze, until you release,  so it it easy to read.

My regards

My regards

---

### Post by admiralspark on 2010-02-03
If you check [here]("http://www.psychocats.net/ubuntu/xfce") you'll find psychocat's neat, quick way to install XFCE, then go [here]("http://www.psychocats.net/ubuntu/purexfce") to uninstall gnome et all.

---

### Post by Sir Jasper on 2010-02-03
Hi again,

My specs are similar to yours (though not quite as good). I actually have Ubuntu with an Xubuntu desktop, but it was  many months ago that I last looked at Ubuntu.

My needs are such that everything runs really well. So if all goes well for you there may be no need to rush to implement admiralspark´s excellent advice.

My regards

---

### Post by daikon on 2010-02-04
> **admiralspark said:**
> If you check [here]("http://www.psychocats.net/ubuntu/xfce") you'll find psychocat's neat, quick way to install XFCE, then go [here]("http://www.psychocats.net/ubuntu/purexfce") to uninstall gnome et all.

This seems to have sorted the problem. I think I somehow grabbed some Gnome stuff with I-bus or I-ibus anthy when I installed Japanese language input.

Now all all I need to do is figure out the Japanese input, but without the CPU overload!

Thanks a lot for all the answers!

Cheers
matt

---

