---
title: "Problems with VNC"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by deejross on 2008-04-01
I'm trying to get the Remote Desktop working on my Ubuntu machine at home from work. I can connect to it over SSH, but I really need to get into my desktop session. I searched all over the internet and found that I could turn it on using this command:
> gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
I did that and now every time I try to log in, the VNC client on my windows machine hangs at "Please wait - Initial screen loading...". I thought that maybe enabling the server wasn't enough, so I edited the "~/.gconf/desktop/gnome/remote_access/%gconf.xml" and added this:
```
<entry name="prompt_enabled" mtime="1203386343" type="bool" value="false">
</entry>
```
Thinking that maybe it was asking for permission on my desktop, but nothing has changed. Any ideas?

Thanks

---

### Post by stalker145 on 2008-04-01
Do you have port 5900 forwarded on your home router to the computer you wish to access?

Also, since I don't know anything about running VNC over SSH, the only suggestion that I can give would be to use NoMachine. It runs through SSH and has all manner of cool tools. If you have SSH access, you can download and install through SSH and then install on your Windows computer normally. There is no configuration that you need to do on the "server" and everything "just works".

---

### Post by deejross on 2008-04-01
1. I am using VNC through SSH, so port forwarding on the router not necessary. It's not a connection issue because it IS connecting. It does the negotiation and all that, it just stops short of showing me my desktop
2. I've used FreeNX in the past, and since I'm not interested in running individual desktop sessions, I have no use for it. As I mentioned in the first post, I need to connect to my currently running session anyways, so NX would not do me any good.
3. Having set up an NX server before, the whole "just works" thing is a load of crap. Sure, it "just works" if you have your keys pre-setup, SSH configured for it, PAM configured for it, and if the client version matches the server version.

---

### Post by deejross on 2008-04-01
Further looking, whenever I run the gconftool command to start the server, it overwrites the %gconf.xml file. Is there a way to start the vino-server with it overwriting the %gconf.xml file?

---

### Post by deejross on 2008-04-01
Since I was unable to find any help anywhere on the internet, I played around with this until I got it to work. I will post the resolution to this problem since it seems like an often asked question. This requires you to be running Ubuntu or Windows + X Server on the machine you want to connect FROM. In my case, I remote controlled the other Ubuntu machine I have running at home. Basically, you will be using X forwarding via SSH to change the settings on the remote machine.

Open terminal and run:
```
ssh -X user@hostOrIP
```

Once you're logged in, simply run this command, which will open the Remote Desktop settings window:
```
vino-preferences
```

Set everything thing up the way you like it, then UNCHECK the box "Allow other users to view your desktop". We will re-enable this is a minute, but first we need to kill the vino-server so that it will apply the new settings.

Close the Remote Desktop Preferences window. Then kill the vino-server by running:
```
killall vino-server
```

Once that's complete, run ```
vino-preferences
``` again, and CHECK the box "Allow other users to view your desktop." Close the window, and you should be able to connect to the machine over VNC now.

---

