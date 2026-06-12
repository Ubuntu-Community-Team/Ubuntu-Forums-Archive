---
title: "Want to share desktop workspace."
date: 2009-07-05
forum: New to Ubuntu
---

### Post by nodnarb22 on 2009-07-05
Okay, I'm in the process of building a new desktop. What I want to be able to do is run a full desktop workstation on it for my self to use but i also want allow my girlfriend to be able to access and utilize the processing power of the computer through her laptop in a thin client manner. I dont know how in the world to go about this. I see edubuntu has the ltsp stuff in it but can you run a "ltsp" server and use it as a workstation?

---

### Post by scrooge_74 on 2009-07-05
You could configure so she can access your drives, or do a remote desktop

---

### Post by scorp123 on 2009-07-05
> **nodnarb22 said:**
>  i also want allow my girlfriend to be able to access and utilize the processing power of the computer through her laptop in a thin client manner.  VNC maybe? All she would need on her laptop is a so called VNC client for whatever OS she has there.

Give this tutorial here a try ... it's step by step and should be easy to follow:

[http://ubuntuforums.org/showpost.php?p=4963842&postcount=1](http://ubuntuforums.org/showpost.php?p=4963842&postcount=1)

Yes, I know ... the stuff up there was written for Ubuntu 8.04. No problem though, it should all work the same on Ubuntu 8.10 or 9.04.

---

### Post by HermanAB on 2009-07-05
Howdy,

VNC is mainly a Windows thing.  On Linux, it is almost always the wrong solution.  Rather than using VNC, install the ssh server package and make an account for her.

Then from the other computer, connect with ssh as follows:
$ ssh -X -C -c blowfish user@server gnome-panel

If the other computer runs Windows, use Xming and PuTTY to achieve the same effect.

VNC server is the main reason Ubuntu machines get hacked.  It is insecure and the are bots looking for VNC connections, so apart from being slow and difficult to get to work, it also insecure.  All, in all, not a good idea at best.

---

### Post by scrooge_74 on 2009-07-05
if she is running linux on the other one she can also do a Desktop session using ssh

if I remember well some instructions I saw once, she goes into terminal mode (without logging into a dektop enviroment), then she logs in the terminal and she will do a:

xinit /usr/bin/xterm -- :1

then ssh -Y user@target_system

then when in there will do a starx or startkde or gnome-session and she would  be using the resources of your PC through the network.

---

### Post by scorp123 on 2009-07-05
> **HermanAB said:**
>  VNC is mainly a Windows thing. From which parallel universe are you? :lolflag:

You are mistaking RDP with VNC, could that be?

> **HermanAB said:**
>  On Linux, it is almost always the wrong solution. Sorry, but you're being ridiculous here.

> **HermanAB said:**
>  Then from the other computer, connect with ssh as follows:
$ ssh -X -C -c blowfish user@server gnome-panel  He said "thin client manner". That includes possibility to disconnect from a session and resume it later. You can't do that with "ssh -X". In the second she gets disconnected whatever she was running is dead and crashes.

> **HermanAB said:**
>  VNC server is the main reason Ubuntu machines get hacked. Sources for that claim please? 

> **HermanAB said:**
>  It is insecure and the are bots looking for VNC connections  True. But irrelevant if you use it at home.

If the goal is to use this remotely via the Internet then yes, then VNC would be a bad idea and OP would have to tunnel it across SSH ("VNC-over-SSH" is safe) or could use FreeNX instead.

But I was under the impression that we're talking about a solution that should be used at home, so VNC's security or lack thereof would not matter.

---

### Post by scorp123 on 2009-07-06
Another tutorial that just got posted:

"Turn Your Old Laptop into a Powerful Linux Workhorse"
[http://blog.worldlabel.com/2009/turn-your-old-laptop-into-a-powerful-linux-workhorse.html](http://blog.worldlabel.com/2009/turn-your-old-laptop-into-a-powerful-linux-workhorse.html)

And yes, that solution uses VNC too ... :lolflag:

---

### Post by nodnarb22 on 2009-07-09
Well weekend is here time to give it a try, i so far have ben unsucsessfull getting ubuntu 9.04 to run on her laptop. graphics issue. cant get it to run in its native resolution for the life of me so far. Hadn't tryed using a diff version of linux on her computer to access the vnc. i know dsl, puppy and i believe ubu 8 works fine on her's. we shall see. Thanks for the help so far guys.

---

### Post by scrooge_74 on 2009-07-09
Go for ver 8.04, I just had to do that on a Dell with an ATI card. 9.04 got ramdon freezes from time to time. With 8.04 running like a champ for 12 hours straight

---

### Post by scorp123 on 2009-07-10
> **scrooge_74 said:**
> Go for ver 8.04, I just had to do that on a Dell with an ATI card. 9.04 got ramdon freezes from time to time. With 8.04 running like a champ for 12 hours straight +1 for that.

I have strange issues too here. My wife's parents have a super old HP OmniBook 4150B laptop: 256 MB RAM, Pentium III CPU 450 MHz, and this laptop has some really really old ATI "Rage Mobility" VGA chipset.

With Ubuntu 8.04 and 8.10 it all works flawlessly, with 9.04 I am having plenty of strange issues. So for now I will keep 8.10 on this old machine. It seems to work pretty well for them (they can read mails, surf the web, use Skype ...). They don't even know what OS they are using or what an "OS" even is in the first place. So for now I don't have to worry about them insisting on upgrading the OS or anything like that.

By the time 9.10 is officially out I hope I can buy them a better laptop. But for now 8.10 will do the job.

---

### Post by kendoori on 2009-07-10
Check out NX. The No machine client and server are free and the performance is much better than VNC.

[http://www.nomachine.com/](http://www.nomachine.com/)

---

### Post by naklinaam on 2009-07-10
Agree with Kendoori.

I have used it in the past and it works like a charm.

Caution.
It is usually a mess trying to get the ssh thing to work with nomachine. I have not been able to do that successfully as yet (I have an open question on this forum trying to get that done)

However, I used the freenx version (open source alternative based on nomachine NX but has some minor limitations like no audio tunnelling etc) on my previous install and was able to get that to work.

Unless someone here can help spell out the steps to make ssh work on nomachine, and unless you absolutely want the additional features supported by nomachine NX, I suggest you try FreeNX instead.

PS: I am still trying to get nomachine to work for me as I want the audio tunneling

update: 
There was nothing wrong with the NX server... I just rebooted the machine and executed ```
sudo /usr/NX/bin/nxserver --usercheck <user>
``` and the server updated my authorized_keys2 file with the public key.

Started working again...

NX Rocks..

Now for the fun part.. need to get the audio streaming to work.

---

### Post by naklinaam on 2009-07-10
Check post # 4 on this thread [http://ubuntuforums.org/showthread.php?t=611198](http://ubuntuforums.org/showthread.php?t=611198) for more info on how to install NX,
OR go directly to [http://www.nomachine.com/ar/view.php?ar_id=AR12D00432](http://www.nomachine.com/ar/view.php?ar_id=AR12D00432)

---

