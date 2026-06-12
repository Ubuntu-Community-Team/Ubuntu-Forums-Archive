---
title: "Why isent Deluge working?"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by VitaminBB on 2009-03-25
I dont get it.

I start up deluge after not using it for awhile and everything is greyed out.

I cant add a torrent, I cant change settings, its all greyed out.

Its on the latest version, worked last time I used it.

Not the slightest clue why it decided not to work, **any ideas?**

[IMG]http://i79.photobucket.com/albums/j121/ArghMonkey/Screenshot-1.png[/IMG]

[IMG]http://i79.photobucket.com/albums/j121/ArghMonkey/Screenshot-2.png[/IMG]

---

### Post by VitaminBB on 2009-03-25
Anyone?

---

### Post by Zack McCool on 2009-03-25
Is the daemon running?  Open the connection manager, and there should be a daemon listed at 127.0.0.1.  Make sure it is started, then connect to it.

If that doesn't do it, you may want to make sure you are running the latest version.  They have had a few updates recently that are not in the repos.  Deluge provides .deb files for installation...

---

### Post by VitaminBB on 2009-03-25
> **Zack McCool said:**
> Is the daemon running?  Open the connection manager, and there should be a daemon listed at 127.0.0.1.  Make sure it is started, then connect to it.

If that doesn't do it, you may want to make sure you are running the latest version.  They have had a few updates recently that are not in the repos.  Deluge provides .deb files for installation...

Yup the Daemon window pops up but all I see is this ...

[IMG]http://i79.photobucket.com/albums/j121/ArghMonkey/Screenshot-3.png[/IMG]

I open options and tell it to start daemon automatically etc and still deluge wont work right ...

Im in the latest version ...


**How do I tell Deluge to connect ?!**


.

---

### Post by lovinglinux on 2009-03-25
Maybe this is due to corrupted settings files. Try deleting the config folder before launching it (I guess is ~/.deluge).

---

### Post by VitaminBB on 2009-03-25
> **lovinglinux said:**
> Maybe this is due to corrupted settings files. Try deleting the config folder before launching it (I guess is ~/.deluge).

I looked for the folder, doesnt exist.

---

### Post by lovinglinux on 2009-03-25
> **VitaminBB said:**
> I looked for the folder, doesnt exist.

Sorry. The correct folder is ~/.config/deluge

---

### Post by harry71194 on 2009-10-08
I don't know if you fixed your problem, but try updating your libtorrent to 0.14.5.0 or higher.

---

### Post by fatihsola on 2009-11-29
Hello everyone, i am using deluge for a while too, and same problem for me, 

too. but i am using Pardus, another distribution of linux. all the system 

is updated and no problem with azureus. (version of deluge: 1.2.0-rc2)

Thanks in advance.

---

### Post by A_T on 2009-12-01
I've developed real problems with Deluge. Greying out everything and not adding torrents. I've tried purging and reinstalling from both the Deluge and Ubuntu repos but nothing worked. Going back to Transmission for now.

---

### Post by Locke_99GS on 2009-12-01
You guys ought to make posts at Deluge's forums where the developers can help you, or you can help them figure out what is wrong. 

BTW; Deluge is at 1.2rc4 now, may want to try that.

---

### Post by A_T on 2009-12-02
I posted there a couple of days ago but no reply from the developers so far.

---

### Post by ASchweitzer on 2009-12-02
I'm also having problems, looking into stuff right now. From what I can tell so far, there's a problem with the *deluged* package. This is the daemon, but it not a dependency of any of the other deluge packages. So I'm not sure what's up with that. I should have it fixed by tonight, will post results.

---

### Post by ASchweitzer on 2009-12-03
Right. Solutions!!

So as of 1.2.0_rc2 (rc2 as far as I know, maybe earlier), the deluge guys have changed the package names in the repositories, as well as the executable names.

The deluge daemon in still *deluged* both in the repos, as well as the executable name.

The web UI however, has changed.

The new executable and package for the web UI is *deluge-web*, and not *deluge -u web* as with older versions.

I've got a working web interface by running
```
deluged
```
and then
```
deluge-web
```
and can subsequently pull up the web UI and connect on port 8112.

As far as the OP, I'd make sure you're running *deluge-web* (rc4 now) and that both *deluged* and *deluge-web* are the same version. If I remember correctly, the *deluge -u web* is still there up to 1.2.0_rc1, so you may have confusion there.
I know that the new-looking web UI will still launch via *deluge -u web* (but I'm pretty sure that the *deluge* package is stuck at rc1 and as of rc2 it's not used). Thus, *deluge -u web* is not compatible with *deluged* so make sure to use *deluge-web*.

There are some excellent guides on automating this process [in this thread]("http://forum.deluge-torrent.org/viewtopic.php?f=7&t=25535") as well as in the [deluged wiki]("http://dev.deluge-torrent.org/wiki/UserGuide/InitScript#DebianUbuntuInitScript").

If you need any help with automating, PM me.

The greyed-out features are being addressed, I think, on the deluge forums. I'm sure they're just things that are being worked out with the new version.

---

### Post by highspider on 2011-03-17
> **lovinglinux said:**
> Sorry. The correct folder is ~/.config/deluge
This worked for same error I had on Ubuntu 10.10 with Deluge 1.3.0

shell commands are in RED
```
[COLOR=Black]#clear the config per lovinglinux[/COLOR]
[COLOR=Red]rm -fr ~/.config/deluge/*[/COLOR]

[COLOR=Black]#list all the installed dpkg of deluge [/COLOR]
[COLOR=Red]~/.config$ dpkg --get-selections | grep deluge[/COLOR][COLOR=Green][COLOR=Black]
deluge                    install
deluge-common       [/COLOR][COLOR=Black]      install
[/COLOR][COLOR=Black]deluge-gtk                [/COLOR][COLOR=Black]install[/COLOR][/COLOR]

[COLOR=Black]#note u might have more like "deluged install" 
[/COLOR] [COLOR=Black]#so include them in reinstall[/COLOR]

[COLOR=Black]#reinstall all deluge packages with new default configs[/COLOR]
[COLOR=Red]sudo apt-get install --reinstall [/COLOR][COLOR=Red]deluge deluge-common deluge-gtk[/COLOR]

```I tried just clearing the config file. worked fine the first run then same problem the second run. thats why I cleared the config then reinstalled

---

### Post by lotharmat on 2011-03-17
I has this issue a while ago - deleting the config folder worked for me!

---

### Post by Shinobi_no_mono on 2011-07-08
My pc froze up in the middle of the night while sleeping, woke up and it was frozen on the screen saver, shut the monitor back off, woke up later to discover it had rebooted itself, weather applet didn't work on first restart, clock applet failed on second restart, so upon rebooting those two times I shut down the pc, waited a few mins, started it back up and then noticed my Deluge wont connect and I get the popup dialog for this connection manager 127.0.0.1....... 

Anyone know how to fix it?

those 2 applets not working and then deluge sounds like some kind of glitch to me, any ideas?

thanks!

---

