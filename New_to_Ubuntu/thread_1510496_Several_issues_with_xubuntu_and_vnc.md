---
title: "Several issues with xubuntu and vnc"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by silversonic on 2010-06-15
Hello everyone:

I've been a loyal ubuntu user for several years, but I still feel like a beginner.  Hence my posting in this forum.

Let me give you my setup:
- I have a box that runs Ubuntu 10.04 and Windows vista (for gaming and itunes), and a laptop that runs only ubuntu, and I want to be able to use those as client machines.
- I have a much older box that runs xubuntu 10.04 that I want to be the 'server'.

I am having a couple of issues trying to get a remote connection to my xubuntu box so I can use it as a general dump for data and be able to remote into from both my local connection (so I don't have to connect it to a monitor) and from the internet as well.  I followed [this guide]("https://help.ubuntu.com/community/VNC") to get a vnc through ssh setup going.  Everything seemed to go well until I hit the snag at 2).

The two problems I have:

1) Through tightvnc, I am able to set up a remote connection over my LAN, but it won't connect to my xfce session on xubuntu.  the vnc viewer will instead set up a separate session running gnome.  This would not be a problem were it not for the fact that prompts for the password still happen on the xfce session, rendering just about anything I do remotely useless.  If I were to either be able to log in to the same xfce session or make it so that password prompts on the default gnome session, or any other workaround that won't stop my connection dead in its tracks, I would be very very happy.

2) Through ssh trying to do remote host to WAN, I am able to setup and verify that my rsa keys work, I ssh to my xubuntu box through the local network fine, but when I try to ssh at [email]user@dyndnsaccount.org[/email], I receive this error:

```
connect to host dyndnsaccount.org port 22: Connection timed out
```

even though, *on that machine*, I have portforwarded port 22 from my router.  I even used iptables to open up port 22 using [this guide]("https://help.ubuntu.com/community/IptablesHowTo"), but still no dice, I get the same error.

Any suggestions for either issue would be greatly appreciated.  I'll answer any questions, run any scripts, etc. if you need anything.  THank you for your time.

---

### Post by bodhi.zazen on 2010-06-15
First I would not use VNC over the internet , tunnel it over ssh at least.

Second, you can forward X applications over ssh

```
ssh -X user@server xfce4-panel
```

You can start a new X session on Ctrl-Alt-F8 

These threads will give you some ideas:

[How-to run Multiple (Virtual) X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=271674") 

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948") 

Not exactly what you are doing, but again just some suggestions.

For vnc, use a different vnc server, such as x11vnc . Some servers attach to a current session (x11vnc) others use a new session (tightvnc, freenx).

In terms of your ssh connection, if you just added the DNS service, it takes a while for the DNS to propagate, you may have to wait up to 24 hours to use it.

Try to connect to your public IP 

ssh use@rpublic_ip_address

Over the internet you can also use compression.

ssh -C -c blowfish user@server

---

### Post by silversonic on 2010-06-15
> **bodhi.zazen said:**
> First I would not use VNC over the internet , tunnel it over ssh at least.

Second, you can forward X applications over ssh

```
ssh -X user@server xfce4-panel
```

You can start a new X session on Ctrl-Alt-F8 

These threads will give you some ideas:

[How-to run Multiple (Virtual) X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=271674") 

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948") 

Not exactly what you are doing, but again just some suggestions.

For vnc, use a different vnc server, such as x11vnc . Some servers attach to a current session (x11vnc) others use a new session (tightvnc, freenx).

In terms of your ssh connection, if you just added the DNS service, it takes a while for the DNS to propagate, you may have to wait up to 24 hours to use it.

Try to connect to your public IP 

ssh use@rpublic_ip_address

Over the internet you can also use compression.

ssh -C -c blowfish user@server

Hey thanks for getting back so quick.  I had to go to work when you replied but I got back and tried your first bit of script on the terminal of the client computer, and then hit control-alt f8 and all I got was a blinking cursor, so I must be missing a step.
 
To be clearer: what I am trying to do is be able to access my old desktop computer remotely so that I don't need to hook a monitor up to it.  How it is accomplished is less of an issue as to what works.

Thanks again for your suggestions, I will read those two posts and see if they are close to what I'm looking for.

edit: sorry I misread your post, I thought you were expressing confusion.  In any case, having nested x sessions is muy neato, I will make that a project once I can sort my current mess out.

---

### Post by silversonic on 2010-06-16
Haha!  I was able to find a resolution for this problem:

> 1) Through tightvnc, I am able to set up a remote connection over my LAN, but it won't connect to my xfce session on xubuntu. the vnc viewer will instead set up a separate session running gnome. This would not be a problem were it not for the fact that prompts for the password still happen on the xfce session, rendering just about anything I do remotely useless. If I were to either be able to log in to the same xfce session or make it so that password prompts on the default gnome session, or any other workaround that won't stop my connection dead in its tracks, I would be very very happy.


By following the instructions from the last post of [This thread]("http://ubuntuforums.org/showthread.php?t=23277"), I was able to get a vnc to run the right session of xfce on my LAN.

I will ask again about the ssh issue in another post.  I am happy enough with resolving problem #1 I will consider this thread solved.

---

