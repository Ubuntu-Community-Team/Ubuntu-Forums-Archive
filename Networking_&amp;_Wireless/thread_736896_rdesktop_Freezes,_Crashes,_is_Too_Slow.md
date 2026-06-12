---
title: "rdesktop Freezes, Crashes, is Too Slow"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by process91 on 2008-03-27
I've been trying to connect from linux to my Windows remote desktop servers and there seems to be no way to do it.

rdesktop never really crashes or freezes the computer, but when I connect I start to see the "Log In" screen but it just hangs while drawing the logo. It gets about half way done with displaying the "Windows 2003" logo when it just stops. The computer still responds, and I can close rdesktop and start it again but it never gets past that one point.

I have changed the color/resolution/depth and all that allows me to do is get a little farther before it stops responding again.

It seems like once a certain amount of data passes through rdesktop it just stops the connection.

I should mention that these remote desktop servers are remote, not on the LAN, and that I am able to access them with almost instantaneous speed on a Windows XP computer.

---

### Post by veloce on 2008-03-27
Are you using the bandwidth options?  If so, which one?

Or do you use a front end to rdesktop?

I use GnomeRDP to manage my rdp connections and have no issues connecting from home to work.

---

### Post by process91 on 2008-03-27
Thanks for responding! I have tried Terminal Server Client, Gnome-RDP, and using rdesktop right from the command line. None of them work. I'm on a fast connection, as is the host. I've attached some example output screenshots from each one. In each case, the performance seems like it's so slow that the connection eventually just gets dropped.

Let me know if any of these options should/shouldn't be set to improve performance.

Options Used
termservclient.png - Froze after clicking "OK" on login. The username and password were correct, it should have logged in.
 - Colors: 16bit
 - Screen Size: Default
 - Sound: No sound
 - Optimize Performance: All options checked
     - Enable bitmap caching
     - Do not send motion events
     - Enable window manager's key bindings
     - Hide window manager's decorations
     - Attach to console


gnomerdp.png - Worked the best, actually got me into the desktop but then ended up freezing after opening a window. Before it froze it was responding, but so slowly that it basically rendered the system useless. It took well over 20 seconds to just get the login box to appear, and 8 seconds to have the start menu come up. My VNC response rates blow this out of the water, but remote desktop *should* be faster.
 - Remote Desktop Size: 640x480
 - Colors: 256
 - Keyboard Type: en
 - Sound: No Sound Output

rdesktop.png - I've played with different options here, they don't seem to do much. Most of the time I get what you see in the screenshot, which is the login box half drawn and then it freezes. Sometimes it also spits back the following error in the command prompt: ERROR: recv: Connection reset by peer.

Here's the command I ran:
```
rdesktop -x m example.rdpserver.com:9876
```

---

### Post by HermanAB on 2008-03-27
I guess you just need to upgrade your copy of rdesktop, since I have never had any trouble with it.

---

### Post by process91 on 2008-03-27
I'm using rdesktop 1.50. It's the newest version in the repo and the newest stable version at [http://www.rdesktop.org](http://www.rdesktop.org).

I'm actually running Hardy Beta, but I have three other computers running Gutsy with the same problem.

Attached is another screenshot of the most typical problem I've encountered. The program simply hangs like this forever.

---

### Post by process91 on 2008-03-31
*bump*

---

### Post by alauro on 2008-04-01
I've had the same kind of problems. I upgraded to Heron because I thought maybe it was a bug in Gibbon, but I've got the same issues with Heron. It seems that when I'm connected to a network via VPN rdesktop freaks out. When I'm simply connecting to another machine on my work network, everything is fine. I hope someone posts and prvoides some information because this is really annoying.

---

### Post by danpre on 2008-04-13
> **alauro said:**
> I've had the same kind of problems. I upgraded to Heron because I thought maybe it was a bug in Gibbon, but I've got the same issues with Heron. It seems that when I'm connected to a network via VPN rdesktop freaks out. When I'm simply connecting to another machine on my work network, everything is fine. I hope someone posts and prvoides some information because this is really annoying.

I have exactly the same problem.
A few days ago i started a post:
[http://ubuntuforums.org/showthread.php?t=748479](http://ubuntuforums.org/showthread.php?t=748479)

I've thought that is a Cisco VPN problem - do you think it is a problem with rdesktop?

danpre

---

### Post by dhn on 2008-04-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/217868](https://bugs.launchpad.net/ubuntu/+bug/217868) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm experiencing the same problem, under Hardy and Gutsy. No problems under Dapper, which suggests the problem may not be in rdesktop. I opened a bug in launchpad:

[https://bugs.launchpad.net/ubuntu/+bug/217868]("https://bugs.launchpad.net/ubuntu/+bug/217868")

---

### Post by koenr on 2008-06-18
For me disabling all sound solved the problem

---

### Post by dhn on 2008-06-18
Hi koenr, can you clarify how you disabled sound? Was it in the control panel of the windows server, or by passing '-r sound: off' to rdesktop on the client? The latter did not fix the problem for me.

---

### Post by process91 on 2008-06-24
Same here, the "-r sound: off" did not change anything.

---

### Post by Plasma_NZ on 2008-07-12
Ok, im havin issues using TSclient and rdesktop...

Im trying to enable sound local from the windows box... but windows keeps saying its busy etc...

any ideas.? im total noob at RD stuff..

---

