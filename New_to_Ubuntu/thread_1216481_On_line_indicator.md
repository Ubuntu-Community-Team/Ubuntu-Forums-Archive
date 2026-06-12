---
title: "On line indicator"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by BobJam on 2009-07-18
Is there a way in Ubuntu to see an on line indicator?

I see in the top panel there is a small icon of offset computer screens and hovering over it tells me that my wired connection is active, and I also see a striped progress bar when I'm downloading.

However, in the Windows systray there was a similar offset computer screens icon that would flash when my router was communicating.  I don't see the icon in Ubuntu doing that . . . it is static . . . no flashing.

This is mainly a cosmetic thing, but I used to glance at that flashing icon in Windows now and then just to make sure my ISP server wasn't down, or my cable wasn't disconnected, if I got a timeout on a web site.  When one of the screens would flash, at least I knew it wasn't on my end.

In lieu of the flash, is hovering over that Ubuntu "wired network connection" icon necessary to see if communication attempts are at least going out?  Or is there a setting that makes the icon flash?

---

### Post by Sidewinder1 on 2009-07-18
This doesn't actually answer your question, but if you search for "Screenlets", you'll find a plethora of them that cover just about anything you can think of from monitoring your network connection/IP address to weather.
HTH,
 Side

[http://www.screenlets.org/index.php/Home](http://www.screenlets.org/index.php/Home)

---

### Post by 3rdalbum on 2009-07-18
I add the System Monitor applet to my panel. It shows network traffic in a graph, which I guess is more descriptive than just an icon flashing :-)  It also shows CPU use if you want it to, which is very handy for being able to tell when you've got a runaway process.

---

### Post by BobJam on 2009-08-09
Found it!!!

(Have been "taking" from this forum, and now I finally have a chance to maybe give something back by telling another Noob how to do something).

OK . . . it was native all along.  Just had to add it to the panel:

[IMG]http://i510.photobucket.com/albums/s346/rbjamie/Ubuntu/Network%20Monitor/Iconinpanel.png[/IMG]

Added it to the lower panel.

Here's how to do it.

Just right click on the panel you want to add it to (top or bottom).  In the pop up menu, slide the pointer up to the top and click on "Add to Panel".

That will bring up the "Add to Panel" window.

Scroll to "Network Monitor", select it, and then click on the "Add" button at the bottom:

[IMG]http://i510.photobucket.com/albums/s346/rbjamie/Ubuntu/Network%20Monitor/Rightclickpanel.png[/IMG]

That will do it.  Now you'll have an indicator that shows if there's connection activity.

**NOTE:**  This is NOT the same thing as your "Network connection" indicator:

[IMG]http://i510.photobucket.com/albums/s346/rbjamie/Ubuntu/Network%20Monitor/WiredNetworkconnectionindicator-1.png[/IMG]

---

### Post by Sidewinder1 on 2009-08-09
Kewl! I'd never noticed that....Just added it...Mega Thanx Bobjam!!!

---

### Post by Ebere on 2010-04-07
I am on Ubuntu 9.10

I tried your suggestion, and while I did find a list of things I could add, I did not find anything even similar to "network monitor".

I found system monitor, added that, and then in preferences, chose network, and unchecked the rest.

But that just gives me a tiny little window with a graph of some sort.

I'd like to have the "two screens" as in your illustration.

Any ideas, anyone ?

---

### Post by audiomick on 2010-04-07
This is just a guess, and I can't try it myself at the moment because I am not at home, but
try having a look in the package manager. Maybe it isn't installed, but available.

---

### Post by BobJam on 2010-04-07
Audiomick made a good guess.

It is now a package (wasn't in previous releases) called "gnome-netstatus-applet" and you have to install it for it to show up in "Add to Panel".  It should be in Synaptic under packages NOT installed (and again it's named "gnome-netstatus-applet")

And there's a nuance to this.  Once you install it, it still won't show up until you reboot (or you could do a killall command on gnome-panel, but I'm not sure of the syntax for that command, so I do a reboot).

Once you reboot, it should show up and then you can add it as you wish.

That should do it.  I tested the method by removing it from the panel and then uninstalling it.  I then reinstalled it, rebooted, and it showed up (I put it back where I had it).

Am curious to know if it is in your Synaptic Package Manager . . . it should be . . . so post back and let us know.

---

### Post by 3rdalbum on 2010-04-07
> **Ebere said:**
> 

I found system monitor, added that, and then in preferences, chose network, and unchecked the rest.

But that just gives me a tiny little window with a graph of some sort.

It graphs network traffic. You can set it up so it shows how much is coming up and how much is coming down. Oh, and even how much of your network traffic is going to local computers rather than to the Internet. Much more descriptive than a simple flickering.

---

### Post by Linuxforall on 2010-04-07
Gkrellm also shows a nice graph of upload and download in real time right on your screen.

---

### Post by Ebere on 2010-04-11
> **Linuxforall said:**
> Gkrellm also shows a nice graph of upload and download in real time right on your screen.

I have not been able to post here, for a while.

Every time I try, whether I hit the submit button, or the preview button, it always comes back with a message that my message is too short. I should lengthen my message to include at least one character.

Whaaaa??? Lot's more than one character in the post. But it gets wiped out, and the message appears.

Hopefully it will go through this time.

Thank you for the responses.

I installed "gnome-netstatus-applet". I rebooted. Still no network monitor.

There is a network manager, (which does no good for what I want.) And there is a system monitor. (The network window of which I am currently using for a graphical indication of traffic.) But there is no network monitor.

I also installed "Gkrellm". It looks promising. But to make it give me the info I want, it looks like I have to learn all that chicken-scratch-gobbledeegook commandline stuff. LOL

IOW, I have to know what to feed it, to get it to feed me what I want. I am nowhere near far enough along after only 4 days of installed and running Ubuntu, to be able to figure that one out. Guess it'll have to wait until later, and I'll settle for the graph that is down there now.

3rdalbum, my tired old eyes do not make much of the different colors in that tiny box. And I don't really want to take up a bunch of the screen by making it larger.

So it is a matter of 6 of one, half a dozen of the other. 

With the graph as small as it is, it gives (at least -my-) eyes, about as much information as two little flickering boxes would. Well, not exactly true. At least I can see when it is just a little bit of color, (traffic), and/or a lot of color. So maybe best that I just leave it this way.

Thanks to all. 

:)

On edit: I did, (obviously) figure out the posting problem. I had marked "yahooapis" as untrusted in No Script. Back to normal now.

---

### Post by skyeric on 2010-04-11
> **BobJam said:**
> 
Am curious to know if it is in your Synaptic Package Manager . . . it should be . . . so post back and let us know.
I've found it too in the same way yes

---

### Post by OzzyFrank on 2010-08-13
> **BobJam said:**
> It is now a package (wasn't in previous releases) called "gnome-netstatus-applet" and you have to install it for it to show up in "Add to Panel".

Thanks for that info, as in an upgraded 10.04 system I still had that monitor in my panel and as an applet I could add, but since doing a fresh install of 10.04 it was missing. This did the trick. Cheers

---

