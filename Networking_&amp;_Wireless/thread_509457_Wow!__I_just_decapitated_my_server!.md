---
title: "Wow!  I just decapitated my server!"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by kvonb on 2007-07-25
For years I've been using a remote desktop programme (vncviewer) to access and administer my server.

A good friend of mine is always nagging me about how much CPU and RAM it wastes doing that, (he's one of these command line junkies!), and I've always resisted switching to a console based server for several reasons.

Reasons such as:

_*** Firestarter***_   I like using the Firestarter GUI, it's easy to add port forwards and see what's going on with the network.

_*** Azureus***_     I like this app because it has the ability to select individual files inside a torrent, ie if I only want 1 file in a 5 gig torrent, Azureus will let me do that.

_***Nautilus***_ For some things, using a file manager like Nautilus makes things easier and quicker.

Well, I was sufficiently peeved off tonight with how slow my server was running, and after several trips down the backyard in the rain, I decided to try a few new ways of doing things, and boy did I hit on some good stuff!

One thing I've always wanted to get working is that remote X display thing, where you can run a GUI app on a workstation over an ssh tunnel or something, but always though it was way too hard to setup.

To my surprise, it's already working, and I came across it by accident!

I thought I'd install **xnc** (X Northern Captain text based file manager), seeing as I used to love working with LapLink back in my DOS days, I thought it might be worth a try.

Bugger me a GUI window of xnc popped up on my workstation when I ran it!  It took a little while to sink in, I must have been disconnected from the server and simply ran it locally surely?  Nope, it showed all the files from the server!  I was pleasantly shocked I can tell you.

So that got me thinking, what else would run like that, so I tried nautilus.  Sure thing, it opened a nautilus window on my workstation with all the contents of my home folder on the server in full glory!

OK, but surely not a root nautilus?  Yup, "sudo nautilus" opened a root window.

Hmm, starting to get adventurous, I wondered what would happen if I ran the Firestarter GUI?  Surely there is no way that would run over an ssh connection?

My jaw dropped when it did actually run, and the most amazing part is that it even put it's icon in the system tray on my workstation!!!!!!   Unbelievable, never in my wildest dreams would I have expected that to happen.

So there it was, happily flashing away, informing me of all the scumbags attacking my system, it also shows me the data rate and count on all 3 network interfaces on the server.

But there's still the Azureus problem I hear you cry.  Well I searched through synaptic for some likely candidates, and after a few failures (10 line long command strings just to do a simple thing!), I found one called _***torrentflux***_.

Seeing as I already had Apache, MySQL, and PHP all installed and working, this might be the go.

Well it wasn't so straightforward to set it up unfortunately, there was a problem with the PHP database creation routine, something about the administrator password.  So I went to their website and on their forum someone had suggested using the tar.gz version, which is the latest one, but also has a simple manual database setup script.

Five minutes later, I was downloading torrents with ease, and it's a very nice web interface, you can do everything you need using your browser.  And best of all you can select individual files within a torrent :).

Well, with the last of the problems solved, it was time to get out the axe and behead the slow unwieldy beast.

Bye bye sluggishness ):P

I saved myself 30% of base CPU usage, and stacks of memory, especially as Azureus is Java based and a complete resource hog.   The server would bog right down when Azureus was re-checking a file, add a VNC connection to that and you're at 99% CPU usage for a long time :(.

I found out the secret to all of this, which I will now reveal..........(drum roll).....

** Putty!**

Yup, I had installed **putty** a few days ago on my workstation because I wanted to have different profiles to connect to the server as different users.  It turns out that I had enabled the remote X server part of it, that is why I didn't have to mess about with special commands etc'.

I'm sure you can do this with a standard terminal/ssh session, but I don't know how, and my memory is not improving with age so lots of new commands are not something I want to tackle.

So I am extremely happy with this new setup, it certainly beats a slow VNC connection!

If anybody wants more info on what I did, or help doing the same thing to their system, just ask, I would be happy to help.

Regards, Kev :)

---

### Post by kevdog on 2007-07-25
How about posting some details ... sounds good to me!

---

### Post by srt4play on 2007-07-25
To do that in a regular ssh session from a terminal, include the -X option as part of the ssh command.

---

### Post by kvonb on 2007-07-27
Details?  Sure, which details did you want to know?

Maybe I should do a how-to, and encourage people to add their remote monitoring apps to the list etc', we could end up with some very useful info.

All I suggest doing in the meantime is installing the apps that I used and trying it for yourself, see how you go.

Once you have everything running as you like, simply stop on your server using:

```
sudo /etc.init.d/gdm stop
```

And to make that premanent, remove, or rather move gdm out of /etc/init.d, like so:

```
sudo mv /etc/init.d/gdm /root/
```

Then when you restart your server, X won't start.  And you have a backup copy in /root.

If you ever need to use X on the server, simply login locally at the server and type:

```
startx
```

Easy as!

Here is a screenshot running GKrellm, a sudo Nautilus, baobab (disk usage thingo), and Firestarter on my workstation running Beryl :)

PS. The 25% CPU usage is from the enemy-territory server, nothing else is going over 1%!

---

### Post by kvonb on 2007-07-27
> **srt4play said:**
> To do that in a regular ssh session from a terminal, include the -X option as part of the ssh command.

Excellent, thanks for that one srt4play :)

---

