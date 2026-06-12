---
title: "WICD don't run ifup and ifdown!"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by es926 on 2008-08-30
Hello,

Here's the problem I'm having. I have two scripts that I really want to run when my computer connects to the internet and disconnects. I did some reading and I got the impression that all I had to do was put a script in /etc/network/if-up.d (or if-down.d) and it would be automated. The scripts run properly if I manually execute ifup -a or ifdown -a though nothing happens when I actually connect or disconnect to a wireless network!

I think that pretty much sums it up. I see that there's an option to run a script after connect in wicd but you have to set it up for each wireless network! Maybe this is a bug? Should wicd be calling ifup/ifdown and it just doesn't? I don't know... I'm really frustrated and any help would be much appreciated!

---

### Post by nicedude on 2008-08-30
did you make your script executable? without doing that it won't run as it is just a text file. Also WICD or network-manager can handle all your wifi and wired network settings for you, and no its not a bug as WICD does not run ifup and ifdown because those take the interface up or down and it does not need to do that to connect to a network. When your PC boots it brings the wifi up and it stays up unless you use commands or a script to bring it down.

I am going to sleep now but if you post what you are trying to do with your script I will try to help you tommorow.

---

### Post by es926 on 2008-08-30
Ahhhh, I think that you might have just shed a little bit of light on the situation. I thought that ifup was supposed to be run automatically AFTER the connection was made not to MAKE the connection. My script is definitely executable and the permissions are correct, as I mentioned before it runs correctly after running "ifup -a". I'm just trying to set up a few remote mounts over ssh using fuse (and do a couple other little things), but I'm certain that this isn't where my problem lies.

There were already automatically created scripts in that directory for starting various internet related daemons (avahi, ssh server, mountnfs, etc...) and it seemed like the people who wrote them were expecting them to be run automatically upon connection. The fact that they don't get run is a little bit troubling. Even if wicd or network-manager wouldn't run ifup doesn't it seem like they would want to at least execute "run-parts /etc/network/if-up.d" after establishing a connection? Or am I missing the point?

---

### Post by imdano on 2008-08-30
wicd doesn't use ifup/ifdown at all.  It has a "scripts" button that you can use to tell it to run a script before/after a connection or when you disconnect.  So if you wanted to you could make it execute all the scripts in there.  Just make sure you're using 1.5.x, since the scripts stuff doesn't work correctly in 1.4.2 and below.

---

### Post by nicedude on 2008-08-30
Everything that WICD or network-manager do can be done instead at the command line with iwconfig including setting encryption keys etc. So you could write a script that sets up your wifi parameters you need and then runs the other commands you want to do to remote mount some stuff etc. That way you should be able to make one script that would just associate with the nearest open wifi AP and for any protected networks you use you would need to make separate ones with keys and essids etc. I got the feeling you are mainly worried about using wifi hotspots as you were worried about WICD needing seperate settings for each network to run your script with it, so if I am right about that then this should work pretty easily. Just read the iwconfig man page to see which commands you need in your script to config.


Hope that helps

---

