---
title: "Send &quot;message&quot; to another local network computer. Sort of like IM but on local level."
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by marianlibrarian on 2007-08-07
I should have said like "net send" not IM.

Is there any application that allows one computer on a local network to send a message to another computer on that same network?

It would be nice sometimes if my staff and I had a way to "talk" with out having to leave the front desk or an office. 

I tried using gaim but that didn't work. Even though two of us have aol accounts. I could get it to work on my winders computer but no success on ubuntu. And it seems silly to use up internet band width to just send a message across the building.

Any ideas?

---

### Post by spd106 on 2007-08-07
I think you can do this with Pidgin (Gaim), but you need the Bonjour plugin and Ubuntu doesn't come with it by default, so you have to build it in yourself.  Possibly Gajim will work out of the box, I don't know as I haven't used it myself. The idea is that it will work similarly to iChat on the Mac.

I think I read somewhere that you can do this with Jabber too, though I'm not sure how.

---

### Post by jfinkels on 2007-08-07
> **marianlibrarian said:**
> I should have said like "net send" not IM.

Is there any application that allows one computer on a local network to send a message to another computer on that same network?

It would be nice sometimes if my staff and I had a way to "talk" with out having to leave the front desk or an office. 

I tried using gaim but that didn't work. Even though two of us have aol accounts. I could get it to work on my winders computer but no success on ubuntu. And it seems silly to use up internet band width to just send a message across the building.

Any ideas?

Most *nix systems have this functionality built-in. Take a look at the program "write":```
man write
```

You can also try to install the program "talk" which is a tad bit more complex:```
sudo aptitude talk
man talk
```

Another interesting program is "wall", which allows you to write on every logged in user's terminal (which can be immensely irritating if you are trying to work on something).```
man wall
```

---

### Post by yabbadabbadont on 2007-08-07
Edit: way too late in my response.  :D

---

### Post by marianlibrarian on 2007-08-08
Thanks for the input.

I can't get write to work. the syntax is write user ttyname. I have googled this term to tears and there are no explanations for ttyname. just a bunch of technical stuff that doesn't make a lick of sense.

I was not able to get talk to install. 

and man wall is not what I need so I didn't even try it but wouldn't be surprised if I couldn't get that to work either.

Any more ideas?

Thanks.

---

### Post by yabbadabbadont on 2007-08-08
> **marianlibrarian said:**
> Any more ideas?

Thanks.

Pick up the phone and call them?  :D  :lol:

---

### Post by Megatog615 on 2007-08-08
How can I give myself permission to use the write command?

Is there is a Windows version?

---

### Post by marianlibrarian on 2007-08-08
The phone? But that is so yesterday.  :)

Smoke signals would be too dangerous. I am considering Coast Guard Flag signals. That way, not only could we send messages, but we can get our exercise too. :-D

---

### Post by loell on 2007-08-08
how about SMS-ing? ;)

---

### Post by marianlibrarian on 2007-08-08
We don't have cell phones :(

---

### Post by spd106 on 2007-08-09
This mailing list thread looks promising
[http://pidgin.im/pipermail/devel/2007-July/002073.html](http://pidgin.im/pipermail/devel/2007-July/002073.html)

Ubuntu Gutsy has Bonjour support built in to Pidgin, though I wouldn't recommend using it till Ubuntu 7.10 is released in October. So if you want this feature you'll have to either wait till then or get Pidgin from the repo suggested in the above mailing list. Windows clients will need the Bonjour for Windows package too.

---

### Post by xyrer on 2007-09-10
and why not a local jabber server?

---

### Post by spd106 on 2007-09-10
I think a server just for simple messaging would be overkill for a LAN. That's why I recommend Zeroconf/Bonjour as it's a LAN based peer-to-peer technology, so it doesn't require an Internet connection.

If you have a good Jabber server set-up guide, please share. That way we all learn.

---

### Post by marianlibrarian on 2007-09-10
Bonjour!

That led me to Avahi.
> Originally, Bonjour had been released under the controversial Apple Public Source License which caused its adoption to be severely hampered on Linux and other Free Software desktops. This led to the development of the Avahi project under the less controversial LGPL license. Nowadays Avahi is the default Zeroconf implementation on all Linux distributions and has even been ported to Apple's own Mac OS X operating system.

Not to mention that the logo is really cute. Anyway, I just downloaded Avahi and will install and test drive it and report back.

I am not sure at this point, but it looks like Bonjour has a version for windows. I don't know if they are compatible or not. I still have one windows xp machine still left on the network. And would like to be able to "talk / chat" with an Ubuntu computer. 

Even if that is not possible, just getting Avahi on the front desk computer would be a big help. We have so many patrons that do not like to leave after their hour on the computer is up. And when someone is standing in line waiting it would be nice to send a little message to the patron and let them know "Time is almost up." or something like that.

Thanks for the help here!!

---

### Post by marianlibrarian on 2007-09-10
> Windows people are as well able to access Zeroconf resources within their IE browser if using the Howl plugin for IE.

Does anybody know where this plugin can be downloaded??

I googled several different search terms but can't find it.

---

### Post by marianlibrarian on 2007-09-10
:confused:

>  Avahi is currently part of the following distributions:

Ubuntu

What part of Ubuntu?

---

### Post by spd106 on 2007-09-10
> Does anybody know where this plugin can be downloaded??
The only zeroconf plugin for IE that I know about is the one include with Bonjour for Windows from Apple, [http://www.apple.com/support/downloads/bonjourforwindows.html](http://www.apple.com/support/downloads/bonjourforwindows.html).

> What part of Ubuntu?
It's integrated into many areas, though they are mostly hidden in the background. If you open the System -> Admin -> Network capplet and look under the General tab of any active interface, then you can enable/disable avahi by ticking the box next to service discovery.

---

### Post by marianlibrarian on 2007-09-10
There is

system > administration > networking (which has a general tab)
and
system > administration > network tools (which does not have a general tab)

I do not see a network capplet and 
> look under the General tab of any active interface, then you can enable/disable avahi by ticking the box next to service discovery.
I can't find that either.

---

### Post by spd106 on 2007-09-10
Sorry my memory is a little hazy pre-Ubuntu 6.10. I think Avahi was disable on 6.06 out of the box. 

Try looking on the /etc/default/ directory for the avahi-daemon file. If it's there then check it's set to autostart. If not look in Synaptic for avahi-daemon.

There are a few resources on zeroconf/avahi in the wiki.

[https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)
[https://wiki.ubuntu.com/ZeroConfNetworking](https://wiki.ubuntu.com/ZeroConfNetworking)

(capplet == configuration applet or so I am led to believe)

---

### Post by marianlibrarian on 2007-09-11
>  Try looking on the /etc/default/ directory for the avahi-daemon file. If it's there then check it's set to autostart.

I will look in the two resource links you gave. - Thanks!

One thing: about autostart - I didn't see where the option for autostart is located. Is this something that can only be done from root?

---

### Post by marianlibrarian on 2007-09-11
avahi-daemon is part of a server install for 6.06 but not part of the desktop install for 6.06. So I didn't have to install it on my Ubuntu server, but I did install it on one of my public access computers that is set up as an Ubuntu desktop. I am understanding that all computers must have this avahi installed to communticate or see each other.

I read and downloaded the resource links and all I am able to find out is that avahi-daemon is on the hard drive. There is no way to access - it - no interface, no command line things, and I have already devoted too much time to try and figure this out anymore.

It would seem --- logical --- to go to administration - networking or networking tools and find some sort of tab or menu item -- something. 

as far as I can see this avahi simply uses up resources and delivers nothing. 

anyone know how to steer me in the right direction please jump in!

Edit:
> If you open the System -> Admin -> Network capplet and look under the General tab of any active interface, then you can enable/disable avahi by ticking the box next to service discovery.Ok, I have looked and the only thing I have that under Network that has a General tab is Networking and all it has is two fields. One says the host name which for me is "ubuntuserver" and domain name which is blank.

Why isn't this part of ---- Network Tools??????

---

### Post by spd106 on 2007-09-11
I've reinstalled Ubuntu 6.06.1 on my laptop and found you are quite right about the lack of gui controls. It looks like you can only start/stop the avahi-daemon from a terminal. I suppose this isn't too surprising as it wasn't in the default installed system.

You can control the daemon either through the init  or dbus systems. So from a terminal issue commands like these.
```
sudo /etc/init.d/avahi-daemon stop
```or
```
sudo /etc/dbus-1/event.d/25avahi-daemon stop
```

The version of Gaim in Ubuntu 6.06 and 6.10 did not have Avahi support built in. So if you want to use Gaim/Pidgin and Avahi, then I suggest that you either build a newer version from source (not trivial) or install a third party deb, such as the one from debuntu.org. If you do this make sure you have all of the dependencies from the Ubuntu universe repository too, for example libavahi-compat-howl0. 
It should also work quite happily with Pidgin on a Windows PC, as long as you also have Bonjour for Windows installed.

Within Gaim, create a Bonjour account for the user just as you would with any other service. The user will then be identified as user@hostname in the Buddy List window.

---

### Post by marianlibrarian on 2007-09-12
I appreciate your response. It sure seems very complicated and a lot more work than I can devote to it right now. I wish I had an IT person to devote to this. Oh well. I have to be a librarian too and do book things.:-$

Thanks for all your help here. I will keep checking back.:grin:

---

### Post by Harpoon on 2007-09-12
To get back to the simple messaging request, here are two links (short, easy)
[http://www.computerhope.com/unix/umesg.htm](http://www.computerhope.com/unix/umesg.htm)
[http://www.computerhope.com/unix/write.htm](http://www.computerhope.com/unix/write.htm)

Everything you need is already installed and ready to go.  Took me a while to remember , as it was a good 7 years ago that I used it.

---

### Post by marianlibrarian on 2007-09-12
I tried that earlier and then again just now. When ever I use the write or talk commands it just tells me that user is not logged in at that terminal. I know that the user IS logged in. I have to let this go for now. It is hard for me to believe that linux the king of networking (to me anyway) is so weak in this aspect.

---

### Post by AnRa on 2007-09-12
You may just install [Pidgin](http://www.getdeb.net/release.php?id=1307) and use the Bonjour protocol. ;)

---

### Post by jerome1232 on 2008-01-22
I'm suddenly liking pidgin for this, does the windows version also include the Bonjour protocol and does it work? any experience with this?

---

