---
title: "PLEASE HELP - I screwed up my 11.04 install, cannot get Launcher, top bar, or Unity.."
date: 2011-06-25
forum: New to Ubuntu
---

### Post by djpurity on 2011-06-25
I cannot get the terminal to come with alt+f2 or any of those commands some how my installation is totally screwed up. I tried to uninstall compiz because I thought that is why my launcher and top bar stopped showing up and then I tried to reinstall it, but it gave me an error message at the end, which I posted in another thread. But it said in the Ubuntu Software manager that it was installed. But I don't think Unity is installed. I can't access anything I don't know what to do. I am a total beginner. I am lost, I only can get online by accidentally doing some hack thru the help menu. I tried logging on as Ubuntu Classic and Classic without Effects, but in any version I log in as, I cannot get a terminal to do the 

unity --reset

unity --reset-icons

And I don't know what to do. I downloaded a version of Ubuntu 11.04 desktop amd64 release, burned to a CD and tried to boot off it, but it just sits there on the ubuntu screen, not loading or doing anything. What did I do? 3 days ago everything was FINE. How did I go to a perfectly fine comptuer to one I cant even use? I don't know how to use any of the appa I installs I don't know how to bring up the software install center again I am totally lost. I don't want to format and lose all my photos and all that, I just want to fix this. What happened? How can I get my system back to normal ???? HELP this is an emergency I have things DUE i have to use my copmputer and I cant I am so scrweed please someone help me hekp me help me hlpe he3rawemopgf ]
awe
al'a'gagk';jagvn;sdv


HELP HELP HEOP ERHE OLP__9121 98i911 911 911 8HELP

I am so upset

I needf my launcher and top bar back. I can't navigate anywhere or access anything anymore. HELP

---

### Post by Shining Arcanine on 2011-06-25
[QUOTE=djpurity;10981983]I cannot get the terminal to come with alt+f2 or any of those commands some how my installation is totally screwed up. I tried to uninstall compiz because I thought that is why my launcher and top bar stopped showing up and then I tried to reinstall it, but it gave me an error message at the end, which I posted in another thread. But it said in the Ubuntu Software manager that it was installed. But I don't think Unity is installed. I can't access anything I don't know what to do. I am a total beginner. I am lost, I only can get online by accidentally doing some hack thru the help menu. I tried logging on as Ubuntu Classic and Classic without Effects, but in any version I log in as, I cannot get a 
Receiving help on forums will take a while. I suggest that you join #ubuntu on irc.freenode.net and speak to people there. Another possibility would be to find your local Linux User's Group and ask them for help. That also could take some time, but you could probably get help from someone in person.

Otherwise, you can wait for people here to help you. I have no idea where to begin with this. I would need to either see the computer in person or talk to you on IRC.

---

### Post by trizrK on 2011-06-25
> **djpurity said:**
> I cannot get the terminal to come with alt+f2 or any of those commands some how my installation is totally screwed up. I tried to uninstall compiz because I thought that is why my launcher and top bar stopped showing up and then I tried to reinstall it, but it gave me an error message at the end, which I posted in another thread. But it said in the Ubuntu Software manager that it was installed. But I don't think Unity is installed. I can't access anything I don't know what to do. I am a total beginner. I am lost, I only can get online by accidentally doing some hack thru the help menu. I tried logging on as Ubuntu Classic and Classic without Effects, but in any version I log in as, I cannot get a terminal to do the 

unity --reset

unity --reset-icons

And I don't know what to do. I downloaded a version of Ubuntu 11.04 desktop amd64 release, burned to a CD and tried to boot off it, but it just sits there on the ubuntu screen, not loading or doing anything. What did I do? 3 days ago everything was FINE. How did I go to a perfectly fine comptuer to one I cant even use? I don't know how to use any of the appa I installs I don't know how to bring up the software install center again I am totally lost. I don't want to format and lose all my photos and all that, I just want to fix this. What happened? How can I get my system back to normal ???? HELP this is an emergency I have things DUE i have to use my copmputer and I cant I am so scrweed please someone help me hekp me help me hlpe he3rawemopgf ]
awe
al'a'gagk';jagvn;sdv


HELP HELP HEOP ERHE OLP__9121 98i911 911 911 8HELP

I am so upset

I needf my launcher and top bar back. I can't navigate anywhere or access anything anymore. HELP
Calm down, lol.
type this in the terminal to get the windows back:
metacity --replace
(metacity is the main window manager)
then go from there.

---

### Post by trizrK on 2011-06-25
> **trizrK said:**
> Calm down, lol.
type this in the terminal to get the windows back:
metacity --replace
(metacity is the main window manager)
then go from there.
oh and you can access the terminal through a recovery console at the login screen, recovery mode when booting up and selecting a kernel, or even this trick: right click, select create a launcher and type bash in the command option and save it as type application in terminal.
hope this helps.

---

### Post by nerdy_kid on 2011-06-25
boot the system and press <ctrl> <alt> <F1>  Login, and do:

```

sudo apt-get install ubuntu-desktop unity
export DISPLAY=:0
unity --reset
sudo reboot

```

You might need internet for that though.  If you do, then what happens when you try to login with Ubuntu Classic with no effects?  Do you get something that looks something like [this]("http://i1-news.softpedia-static.com/images/extra/LINUX/large/ubuntu1010alpha1-large_001.jpg")?

---

### Post by djpurity on 2011-06-25
got into a terminal screen by pressing shift+f2 for some reason, although all the help guides say alt+f2, and I entered unity --reset and then it gave a bunch of errors. It said it was default in unity so switching to metacity while resetting, but then it said console-window not defined and the screen went black.  I tried other thinsg like unity --reset-icons and it said there was another terminal open with compiz or something.... I can't quote it because I don't have  the screen in front of me or photo memory.

I can't believe it took me the time to post that, go immediately into that screen, reboot, and now when it comes up, the top bar and the launcher are back!!! I am amazed it finally worked, but there are always so many errors running everything in this I don't ever know if it really is fully installed or has errors. Like when I uninstalled compiz and reinstalled it, and it gave both uninstall and reinstall errors. But it seems to be installed. 

So I have the desktop download of natty 11.04 for amd64 iso on my desktop, and I can mount it on my dekstop and all, but it doesn't boot from it (I burned it to a CD and booted from the CD drive with it). It just hangs. So how can I use this to reset the O/S to 11.04 from this iso file? So I can start fresh with everything? I can keep all my photos and files and work and stuff when updating or fixing the O/S right?

I am amazed by the time I logged back on and was amazed to see the top bar and the launcher back, and I had to rebuild my launcher to add Chrome to it, but I went immediately to this thread to DELETE IT before ANYONE COULD READ IT because I thought, oh how embarrassing for freaking out, then fixing it immediaetly afterwards, but already there were at least 4-5 replies in THAT SHORT AMOUNT OF TIME, WOW -- and still, no one told me how to get into a terminal -- oh wait, by the time I finished writing this reply I got a few more replies and some more info on how to do it... alt+f2 does not work on my computer, but all the articles say that is how to get into a terminal window.... why is it shift+f2 for me? It's weird. I am not sure I want to run or play with compiz again, but I guess it's installed by default anyway.... so I guess this is solved.

I did try booting in classic and classic without effects and each time just a screen that had nothing on it. Like a screen with no launcher on the left side and top bar on the top. Just the rest. So no access to any menus or things like that. I used to know how to make a launcher manually to get into compiz once to fix it after accidentally trying the cube desktop thing... man that compiz is deadly with this release... but i never just was unable to reset or fix it before now. So now it is fixed.... I think...

But thanks everyone... and I am embarrassed as hell for freaking out like that.

---

### Post by trizrK on 2011-06-25
> **djpurity said:**
> got into a terminal screen by pressing shift+f2 for some reason, although all the help guides say alt+f2, and I entered unity --reset and then it gave a bunch of errors. It said it was default in unity so switching to metacity while resetting, but then it said console-window not defined and the screen went black.  I tried other thinsg like unity --reset-icons and it said there was another terminal open with compiz or something.... I can't quote it because I don't have  the screen in front of me or photo memory.

I can't believe it took me the time to post that, go immediately into that screen, reboot, and now when it comes up, the top bar and the launcher are back!!! I am amazed it finally worked, but there are always so many errors running everything in this I don't ever know if it really is fully installed or has errors. Like when I uninstalled compiz and reinstalled it, and it gave both uninstall and reinstall errors. But it seems to be installed. 

So I have the desktop download of natty 11.04 for amd64 iso on my desktop, and I can mount it and all, but it doesn't boot from it. It just hangs. So how can I use this to reset the O/S to 11.04 from this iso file? So I can start fresh with everything? I can keep all my photos and files and work and stuff when updating or fixing the O/S right?

I am amazed by the time I logged back on and was amazed to see the top bar and the launcher back, and I had to rebuild my launcher to add Chrome to it, but I went immediately to this thread to DELETE IT before ANYONE COULD READ IT because I thought, oh how embarrassing for freaking out, then fixing it immediaetly afterwards, but already there were at least 2 replies and still, no one told me how to get into a terminal... alt+f2 does not work on my computer, but all the articles say that is how to get into a terminal window.... why is it shift+f2 for me? It's weird. I am not sure I want to run or play with compiz again, but I guess it's installed by default anyway.... so I guess this is solved.
Yes it reset because that was only temporary.

---

### Post by dFlyer on 2011-06-25
To get to a terminal press ctl-alt t.

---

### Post by djpurity on 2011-06-25
> **nerdy_kid said:**
> boot the system and press <ctrl> <alt> <F1>  Login, and do:

```

sudo apt-get install ubuntu-desktop unity
export DISPLAY=:0
unity --reset
sudo reboot

```

You might need internet for that though.  If you do, then what happens when you try to login with Ubuntu Classic with no effects?  Do you get something that looks something like [this]("http://i1-news.softpedia-static.com/images/extra/LINUX/large/ubuntu1010alpha1-large_001.jpg")?


No that is not what it looks like. There is NO TOP BAR, no drop down menus, no time, no bar at all. Just a window with nothing around it. A desktop with nothing else. No icons no bars no anything on it. Or around it. At best I could right click on the desktop to create a launcher manually.... or somehow I randomly hit enough keys to bring up the help menu, which I went thru and it was NO HELP AT ALL with my situation, but I got to the Internet help thru that, which got me to be able to enter this website and how i was able to post for help! But no, I had no screen like that. Just subtract the entire top bar and the menus and everything other than the background image. That's what I had.

---

### Post by djpurity on 2011-06-25
ctrl+alt1+t does not bring up a terminal
alt+f2 does not bring up a terminal
ctrl+alt+f1 does not bring up a terminal

on my machine it was shift+f2 -- why is that?

---

### Post by trizrK on 2011-06-25
> **djpurity said:**
> ctrl+alt1+t does not bring up a terminal
alt+f2 does not bring up a terminal
ctrl+alt+f1 does not bring up a terminal

on my machine it was shift+f2 -- why is that?
i'm sure you can set up a hotkey for a terminal through well the terminal;)

---

### Post by trizrK on 2011-06-25
> **trizrK said:**
> i'm sure you can set up a hotkey for a terminal through well the terminal;)
I searched on google..
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) will set up a hotkey

---

### Post by fabricator4 on 2011-06-26
> **djpurity said:**
> ctrl+alt1+t does not bring up a terminal
alt+f2 does not bring up a terminal
ctrl+alt+f1 does not bring up a terminal

on my machine it was shift+f2 -- why is that?

You might be running with a setup with a different keyboard mapping, such as if you are using a language other than US/English.

Some keymaps even change things like the caps lock key, So that to use caps lock you need to use a key combination.

If so, try to find the documentation for the keymap you are using as it might give you the equivalent key combinations for doing things like this.

Chris.

---

### Post by EllipsisON on 2011-07-10
I am SO relieved I found this page! I did exactly the same thing! I got to terminal by pressing alt+ctrl+f2 then I had to log in. Once logged in I typed unity --reset and this ran for a while but it stopped, leaving me free to type text but without any of the usual terminal prefix (i.e.username@username:~$) so I had to hold down the power button to switch the machine off. Once I switched it back on everything loaded correctly - my unity settings had been reset but at least I had both launcher and top bars back!
Thanks for your help!

---

