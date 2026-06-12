---
title: "minimal karmic"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by dzon65 on 2010-01-11
i'm trying to install this minimal karmic on an old low specs pc.Must have done something wrong,cause I'm not getting to the main screen.Does anybody know a good tutorial on how to install it?Most of the things I could find were for previous releases.Some of the commands aren't recognized.

---

### Post by skymera on 2010-01-11
> **dzon65 said:**
> i'm trying to install this minimal karmic on an old low specs pc.Must have done something wrong,cause I'm not getting to the main screen.Does anybody know a good tutorial on how to install it?Most of the things I could find were for previous releases.Some of the commands aren't recognized.

What do you mean by "main screen"? Login screen?

As far as i know, minimal Ubuntu is well.. minimal

According to this: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Minimal is supposed to download packages during install. If your net connection wasn't working, that might explain why this system is bare bones.

---

### Post by wojox on 2010-01-11
If your staring at a terminal with a blinking cursor, you haven't done anything wrong. Did you call any packages during the setup?

---

### Post by dzon65 on 2010-01-11
Yep,the login screen.That's the tutorial I used along with this one:[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) .I'll give it another try but if it shouldn't work,I'd consider fluxbuntu.But that seems a little heavier.Anyhow,for example "start x" isn't recognized.The network is connected so...As for the rest,did exactly what was said in the tutorial.Let me try this again,I'll post the outcome in an hour or so.Thanks in advance.
Kind regards,John.

---

### Post by skymera on 2010-01-11
A desktop environment isn't included in the Minimal version :)

---

### Post by slakkie on 2010-01-11
> **skymera said:**
> A desktop environment isn't included in the Minimal version :)

Yes it is. You get a tasksel screen where you can define what your machine will do, server, desktop, etc. It just doesn't provide the packages on disk, you fetch them from a repo instead.

---

### Post by dzon65 on 2010-01-11
> **slakkie said:**
> Yes it is. You get a tasksel screen where you can define what your machine will do, server, desktop, etc. It just doesn't provide the packages on disk, you fetch them from a repo instead.
Correct.And that might be the cause,could be I selected server.But still,command not recognized?Not sure if that tutorial works for the 9.10-version.

---

### Post by skymera on 2010-01-11
> **slakkie said:**
> Yes it is. You get a tasksel screen where you can define what your machine will do, server, desktop, etc. It just doesn't provide the packages on disk, you fetch them from a repo instead.

My mistake.

> **dzon65 said:**
> Correct.And that might be the cause,could be I selected server.But still,command not recognized?Not sure if that tutorial works for the 9.10-version.

Now i'm sure the server doesn't include a GUI. :P

---

### Post by Paqman on 2010-01-11
> **dzon65 said:**
> Does anybody know a good tutorial on how to install it?

Yep, I wrote one myself a little while ago:

[Ubuntu Minimal]("http://andyduffell.com/techblog/?p=361")

---

### Post by ankspo71 on 2010-01-11
Hi,
Are you wanting a desktop installed?

sudo apt-get update:

sudo apt-get install gdm gnome-core
(a very basic gnome desktop)

sudo apt-get install gdm xfce4
(a very basic xfce desktop)

GDM is the display manager that allows you login and start your desktop graphically, and is the one you see in the full Ubuntu install. Then there are lightweight desktops like openbox, fluxbox, blackbox, lxde, etc. I'm not familiar with servers, so I can't help much there.

---

### Post by nothingspecial on 2010-01-11
You need to install xorg

---

### Post by mörgæs on 2010-01-11
Here is something that might get you going:

[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

There is some noise in the first thread, but it is still worth reading.

---

### Post by dzon65 on 2010-01-11
No luck.Can't get to the login screen.And there's a bios error as well.Host SMBus not enabled.Before I started installing,I did all the bios updates I could find for this machine so.....What to do?Starting allover again.This has to and WILL work.

---

### Post by dzon65 on 2010-01-11
> **Paqman said:**
> Yep, I wrote one myself a little while ago:

[Ubuntu Minimal]("http://andyduffell.com/techblog/?p=361")

This configuration looks ok.Was planning to use xfce but....Would your configuration run smoothly on 128mb ram 10G Hd.Firefox should run on 128mb,but how about the whole?

---

### Post by mkvnmtr on 2010-01-11
I have done a number of minimal installs. Just did a 9.10 in a virtual box. There are a number of tutorials to get you started. Go for the CLI install. The disk has always picked up my wired connection on several computers. Do not know if it will detect wireless. I installed fluxbox this time and it works fine. Opera will use less resources that Firefox. In fact with the browser open Htop says I am using about 70Mb.

---

### Post by dzon65 on 2010-01-11
That's cool.However,I did the install and finally managed to log in.But when I do,only a terminal opens.
Starting again AAAAAAAAHHHHHHHHH.I'll try this:[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
However,I like the configuration paqman suggested.sudo apt-get update && sudo apt-get install gdm xorg gnome-core gnome-codec-install indicator-session-applet update-manager firefox-3.5-gnome-support gnome-themes network-manager gdebi.I supose somethings missing.When setting these commands,it will not open the log in screen.

---

### Post by nothingspecial on 2010-01-11
This is what I did on my netbook, if it is of any help.

Install minimal with a wired connection

```
sudo apt-get upate and sudo apt-get install wicd
```
```

wicd-curses
```

You can then set up your wireless.

```
sudo apt-get install xorg openbox firefox
```

```
nano ~/.xinitrc
```

add the line ```
openbox-session
```

```
startx
```

That`s it.

But it depends what you want to use the computer for. I use my netbook for surfing the web, maybe a bit of music and logging into my server via ssh, so I figured I don`t really need anything else that isn`t cli based.

---

### Post by dzon65 on 2010-01-11
I wonder what's causing this to open with nothing but a terminal.Followed exactly these steps.It's not exactly what I want but I can always change it later.

---

### Post by snowpine on 2010-01-11
> **dzon65 said:**
> I wonder what's causing this to open with nothing but a terminal.Followed exactly these steps.It's not exactly what I want but I can always change it later.

I think you misunderstand what a "minimal install" means. It is *supposed* to be just the terminal (until you install and configure X and a desktop environment).

---

### Post by dzon65 on 2010-01-11
Finally got it to work! One thing though,the screen isn't spread well,it turns a bit towards the right.Tried resolution but it remains to the right.

---

### Post by Paqman on 2010-01-11
> **dzon65 said:**
> This configuration looks ok.Was planning to use xfce but....Would your configuration run smoothly on 128mb ram 10G Hd.Firefox should run on 128mb,but how about the whole?

You'd probably be swapping to disk a lot on 128MB of RAM, so don't expect the system to be particularly snappy. The minimal Gnome desktop will take up about 80-100MB on it's own. As soon as you opened a browser window you'd be into swap space.

---

### Post by dzon65 on 2010-01-11
> **Paqman said:**
> You'd probably be swapping to disk a lot on 128MB of RAM, so don't expect the system to be particularly snappy. The minimal Gnome desktop will take up about 80-100MB on it's own. As soon as you opened a browser window you'd be into swap space.

Well,installed xfce4 for now but I never really liked it,so,tommorow I'll get some ram,512mb (can't go higher on this) should do the trick.

---

### Post by Paqman on 2010-01-11
> **dzon65 said:**
> Well,installed xfce4 for now but I never really liked it,so,tommorow I'll get some ram,512mb (can't go higher on this) should do the trick.

You should notice a huge improvement. Make sure you keep at least another 512MB swap partition though.

---

### Post by dzon65 on 2010-01-11
What would be a light replacement for totem?With some codec support.

---

### Post by nothingspecial on 2010-01-11
mplayer.

---

