---
title: "Internet Died in 9.10"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by perito on 2009-10-30
Just updated to Ubuntu 9.10, I can connect to my wireless network successfully, but when I try to browse or update the package manager, it seemes as if there is no internet connection.
Firefox is stuck at "Connecting to www.google.com"

Internet worked perfectly on both Ubuntu 9.04 and Windows.
Here is a screen shot, everything looks normal.
What might be the problem??

---

### Post by manoriax on 2009-10-30
Maybe you have restricted the IP address your PC has got to connect to the internet? Check your router configurations.

---

### Post by Cuddles McKitten on 2009-10-30
Have you tried typing in the exact IPs of websites you want to visit?  I had DNS difficulties when upgrading to Karmic.

I ultimately ended up solving it by modifying my NetworkManager setup to include OpenDNS DNS servers since it couldn't handle my local ISP's anymore for some reason.

---

### Post by Matt__ on 2009-10-30
any reason why you upgraded to 9.10 if things were "working perfectly"?

---

### Post by John Bean on 2009-10-30
> **Matt__ said:**
> any reason why you upgraded to 9.10 if things were "working perfectly"?
That's particularly unhelpful. People upgrade all sorts of things for all sorts of reasons, functionality being only one of them. The OP's reasons for the upgrade have little or no relevance to the problem in hand in this case.

---

### Post by John Bean on 2009-10-30
> **perito said:**
> What might be the problem??
I think it's worth rebooting your router, that's what I'd try first.

---

### Post by perito on 2009-10-30
The router is fine, I have a dual boot with Windows and the internet is working fine there (I'm using Windows now)
The router has also no restirictions.

@I ultimately ended up solving it by modifying my NetworkManager setup to include OpenDNS DNS servers since it couldn't handle my local ISP's anymore for some reason. 

Can you explain this more? Maybe I can try to do as you did, what/how did you modify?

---

### Post by Cuddles McKitten on 2009-10-30
> **perito said:**
> 
Can you explain this more? Maybe I can try to do as you did, what/how did you modify?

Assuming you use NetworkManager applet in GNOME:

1. Right click your NM applet
2. Select "Edit connections"
3. Select the network interface you use.  If you use a wired connection, it'll be in the wired tab.  If you use wireless, it'll be in the wireless tab.
4. Click "Edit"
5. Go to IPv4 settings
6. Put this in your DNS servers box: "208.67.222.222, 208.67.220.220" without quotes
7. Change your search domains to "local" without quotes.

Hit apply and see if that does it for you.

---

### Post by nwu on 2009-10-30
I'm having the same problem--wireless seems to work, but the Internet doesn't seem to come up regardless of what I do.

I tried the advice in the above post as well, but nothing happened. It always seems that I can connect to my network but never access the Internet. (Oddly enough, I've also noticed that if I change the connection settings to ad-hoc, that connection is dropped, and a new one with the 'Infrastructure' setting is created.)

---

### Post by k3lt01 on 2009-10-31
Try [this]("http://ubuntuforums.org/showpost.php?p=3996845&postcount=5") and see if it helps. If it does let us know, I use it anytime I have this problem with a new release.

---

### Post by nwu on 2009-10-31
I tried that out and it gave me an Internet connection for about a split second--long enough to load part of the Google homepage and then die again. I'm restarting and trying it out again to see how things go.

---

### Post by nwu on 2009-10-31
OK, it's doing the same thing again, loading up only part of the homepage before the Internet connection is lost again (and it seems that Pidgin is completely unable to connect).

Any ideas?

---

### Post by nwu on 2009-10-31
Now it looks like I can almost completely use Google (the homepage loads up fine, and I am able to view search results), but for some reason the circular loading button never seems to disappear, and I still can't view any other sites / use Pidgin.

---

### Post by nwu on 2009-10-31
Seems like the page never finishing its loading seems to be due in part to images.

---

### Post by JayZen on 2009-10-31
Hmmm Ubuntu says "Now connected" using my wireless connection. But when I try to get to my homepage it wont load. 

*sigh*

Very frustrating. I could just go back to Jaunty. And I'm supposed to be giving a presentation on Ubuntu to my class lol

---

### Post by k3lt01 on 2009-10-31
> **nwu said:**
> I tried that out and it gave me an Internet connection for about a split second--long enough to load part of the Google homepage and then die again. I'm restarting and trying it out again to see how things go.What one did you try? did you disconnect using Network Manager and then reconnect?

---

### Post by nialui on 2009-10-31
> **nwu said:**
> Now it looks like I can almost completely use Google (the homepage loads up fine, and I am able to view search results), but for some reason the circular loading button never seems to disappear, and I still can't view any other sites / use Pidgin.

I have exact same problem and condition like this.. Now I am forced back using Vista.

Lesson learned: the next time you want to upgrade (or fresh install, like me), try booting with live CD first.

---

### Post by bilalakhtar on 2009-10-31
Yes, I think using OpenDNS might solve the problem. I am currently on Ubuntu 9.04, will move to Karmic today evening (i have a slow internet connection) My friend also had the same problem (he has 9.10), I gave him the OpenDNS addresses, and it worked!:o

---

### Post by nialui on 2009-10-31
> **k3lt01 said:**
> Try [this]("http://ubuntuforums.org/showpost.php?p=3996845&postcount=5") and see if it helps. If it does let us know, I use it anytime I have this problem with a new release.

Thanks [k3lt01]("http://ubuntuforums.org/member.php?u=397303"), it works!

---

### Post by k3lt01 on 2009-10-31
Your welcome nialui, glad I could help.

---

### Post by nwu on 2009-10-31
> **k3lt01 said:**
> What one did you try? did you disconnect using Network Manager and then reconnect?

Yep, that's what I tried (modify file, disconnect, reconnect, reopen Firefox). I tested it out again just now, and I'm still able to access Google only (and not even all of the images either).

Any ideas? I really need my Internet connection back. :(

---

### Post by nwu on 2009-10-31
I have no idea what happened, but my Internet appears to fully work now! Thanks for the help, k3lt01. I'll let you know if any problems occur again.

---

### Post by nwu on 2009-10-31
> **nwu said:**
> I have no idea what happened, but my Internet appears to fully work now! Thanks for the help, k3lt01. I'll let you know if any problems occur again.

After a restart, we're back to only Google working again. I'm quite confused now as to what's going on.

---

### Post by nwu on 2009-10-31
OK, after several retry attempts, I finally got it working again. What's strange is that both times I got it to work, I had to plug in my old network card, unplug it, and then plug in my current one before the connection finally worked.

---

### Post by k3lt01 on 2009-10-31
Check the file that you modified, did it save the changes? Sometimes I have had that happen to me and while I am certain, at the time that is, that I did everything properly I had missed something that caused it to revert back to what it was originally. So I would suggest at this moment that you go through the procedure again, step by step, making sure everything is done like in the post I linked for you.

Let me know how you go.

Edit: we just posted at the same time so I have only just seen your latest post. Your new finding doesn't make sense to me, it suggests you have a hardware issue. I don't understand why Google will load but not properly until you physically disconnect a card and then reconnect it while another card is connecting.

---

### Post by nwu on 2009-10-31
> **nwu said:**
> OK, after several retry attempts, I finally got it working again. What's strange is that both times I got it to work, I had to plug in my old network card, unplug it, and then plug in my current one before the connection finally worked.

(Sorry, by "network card" I meant "wireless card.")

---

### Post by nwu on 2009-10-31
Actually, seems like it works as long as I plug in my wireless card AFTER the computer boots up.

---

### Post by perito on 2009-11-02
> **Cuddles McKitten said:**
> Assuming you use NetworkManager applet in GNOME:

1. Right click your NM applet
2. Select "Edit connections"
3. Select the network interface you use.  If you use a wired connection, it'll be in the wired tab.  If you use wireless, it'll be in the wireless tab.
4. Click "Edit"
5. Go to IPv4 settings
6. Put this in your DNS servers box: "208.67.222.222, 208.67.220.220" without quotes
7. Change your search domains to "local" without quotes.

Hit apply and see if that does it for you.

This worked, thanks

---

