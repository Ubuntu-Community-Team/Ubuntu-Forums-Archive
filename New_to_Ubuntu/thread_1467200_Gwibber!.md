---
title: "Gwibber!"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by vivek40 on 2010-04-30
Hii all, Just did a fresh install of lucid lynxx on my system. Howver the problem is here, while I am able to add my twitter accounts etc in gwibber, (through the memenu and even gwibber itself), it actually does not show any messages , in there. I have refreshed the gwibber app umpteen times but still no, gwibber does not show any mesages....although when i tried with live cd everything was working properly.. thanks

---

### Post by Kafubie on 2010-04-30
I just posted something like this just now.
[http://ubuntuforums.org/showthread.php?t=1467205](http://ubuntuforums.org/showthread.php?t=1467205)
8-[

---

### Post by vivek40 on 2010-05-01
Bump!!!! guys someone please help... gwibber just does not work.. i can add my account through "Broadcast accounts" .. but after that when i open gwibber there is nothing there.. no tweets nothing

---

### Post by gastly on 2010-05-01
I have the same problem, the problem is with Gwibber itself...it's a really buggy app (imo). Also there's no other 'good' Twitter/Identi.ca clients that supports the many features that Gwibber provides except for Choqok (which is a KDE app), so we're stuck here.

I'm thinking of migrating to Choqok, since it's simple and has a lot less bugs than Gwibber.

---

### Post by vivek40 on 2010-05-01
so is there no solution

---

### Post by vivek40 on 2010-05-01
Hii I tried starting gwibber from the terminal and I get the below error..

[FONT=monospace]
[LIST=1]
[*]~$ gwibber
[*] 
[*]** (gwibber:2970): WARNING **: Trying  to register gtype 'WnckWindowState' as enum when in fact it is of type  'GFlags'
[*] 
[*]** (gwibber:2970): WARNING **: Trying  to register gtype 'WnckWindowActions' as enum when in fact it is of type  'GFlags'
[*] 
[*]** (gwibber:2970): WARNING **: Trying  to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is  of type 'GFlags'
[*]No dbus monitor yet
[*]Updating...
[*]Updating...
[*]ERROR:dbus.proxies:Introspect error on  com.Gwibber.Accounts:/com/gwibber/Accounts:  dbus.exceptions.DBusException:  org.freedesktop.DBus.Error.ServiceUnknown: The name com.Gwibber.Accounts  was not provided by any .service files
[*]ERROR:dbus.proxies:Introspect error on  com.Gwibber.Streams:/com/gwibber/Streams: dbus.exceptions.DBusException:  org.freedesktop.DBus.Error.ServiceUnknown: The name com.Gwibber.Streams  was not provided by any .service files
[/LIST]

Well need someone's eyes on this..
[/FONT]

---

### Post by gastly on 2010-05-01
No I don't think there is, until the gwibber devels fix this (It's an open bug I think, but I forgot the bug no.).

You can try this:
delete the directories:
```

~/.gconf/apps/gwibber
~/.cache/gwibber

```

and then try.

---

### Post by bloodorange on 2010-05-01
I'm having the same problems with Gwibber.  I've added my Twitter account, but no messages get displayed.  With Facebook, I follow the routine in Gwibber to add the account, but it just doesn't work.

There's a bug post on Launchpad, but I can't find a solution yet.

[https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/530195](https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/530195)

---

### Post by jvc26 on 2010-05-01
If its broken, file a bug against gwibber using:

```
sudo apport-bug gwibber
```

And get it uploaded to launchpad. That way things will actually get fixed rather than just languishing in a forum thread.

Best,

J

---

### Post by durand on 2010-05-01
If you're desperate for twitter/identi.ca, try pino. It's similar to gwibber but is a lot less buggy.

---

### Post by bloodorange on 2010-05-01
I've now discovered that my Gwibber issues might actually be caused by my router, and is not a problem with Gwibber after all.

Below is a copy of what I just posted to Launchpad.  After reading, any help would be appreciated:

[I]I must apologize for blaming Gwibber/Ubuntu for my problem. I'm almost 100% sure that my problem is caused by my router and not a bug in Gwibber.

I connect to the internet via a D-Link 655 router, which is connected to my Virgin Media cable modem. It occurred to me to try connecting my laptop directly to the cable modem, bypassing the router. After doing this, Gwibber works perfectly! I can send/receive "tweets", and I can now set up Facebook easily, which also works fine.

Now my problem is that I when I reconnect the modem to the router, Gwibber doesn't work again. So, this must be a firewall setting or something in the router that needs changing. However, I don't know what to change safely without leaving myself exposed...

I've been using OpenDNS, and wondered if that was blocking Gwibber, but that isn't the case because if I change back to Virgin Media's DNS servers it makes no difference.[/I]

---

### Post by vivek40 on 2010-05-01
Cool bloodorange,...for me it worked great with the live CD .. i just dont understand why it is not working after the installation.. am just going to file a bug ..!

---

### Post by cygnis1 on 2010-05-02
Is there another app that supports Facebook?
Thanks,
Cygnis1

---

### Post by sundar261 on 2010-05-03
Same here.  It was working when I tried the live cd.  Moved from Karmic to get the benefits of "social networking" on Lucid...

Gwibber never worked on Karmic too!!

---

### Post by jose1968us on 2010-05-06
I have the same problem of not getting my messages from Facebook. 
I am behind a router (FritzBox). I am not using network-manager to get my IP address, instead I configured it to get it via dhcp in /etc/network/interfaces. The thing is when I configured manually (in /etc/resolv.conf) a DNS in the Internet instead of using the default one from the router, I start getting my Facebook messages. This dowsn't happend when I use network-manager to get my IP address.

---

### Post by cygnis1 on 2010-05-06
I just tried Lucid Lynx this morning (live cd) and Gwibber works fine.  Not sure what the problem is With Karmic, so will switch to Lucid in a few weeks and will give it a go again.

---

### Post by vivek40 on 2010-05-06
Hii I was finally able to resolve my gwibber issues.. All I did was go to the language settings .. change it to English(United states), and slide the language settings in the order(ENGLIsh(UK),ENGLISH(INDIA), English).. and then again change things back to its original position.. surprisingly ever since that it had been workig properly. However I have uninstalled gwibber as of now and that is because i have found that it eats up a lot of resources.....both memory and CPU from time to time...I guess I would wait for it to get a little more refined although it is a great app to have on your desktop and its integration with memenu is real cool.

---

### Post by x-shaney-x on 2010-05-06
Yeah, so much for "social from the start".

I noticed gwibber was updated a couple of days ago and I only just got around to trying it out.
I was hoping some of the problems would be fixed but it's even worse.

Before I was at least able to post things from it, even though it never updated anything posted after but today, nothing I have posted has actually gone onto facebook.

I just wish ubuntu would stop broadcasting all these exciting plans for the future and concentrate on finishing off the apps they have in their current release.

<EDIT>
Just noticed my comp grinding to a halt. everything jumping around and acting horribly so I looked at the system monitor and guess what was at the top, eating up all my CPU?
That's right, gwibber service and it has only been running about 15 minutes.

This app really has no place in a final release in it's current state let alone being a major "feature".

<EDIT #2>
Well since I last posted on here, I have been trying the rest of the night to do anything with gwibber.
After 20 to 30 (!)  attempts, I am still yet to see a single posting go onto facebook.
I have twice wiped out everything to do with it in my home directory and set it up from scratch and nothing.

I'm not a programmer and I kinda feel bad criticizing someone else's work but I have to say gwibber is one of the worst apps I have ever used (or tried to).

---

### Post by tonsil on 2010-05-06
Pino is great! Seriously go get it.

---

### Post by vivek40 on 2010-05-07
Though I have uninstalled gwibber from my system but I feel that it is actually a real cool application. Yes there are a few changes that it needs, someone has to particularly look into its resource hogging behaviour. If that is sorted out , I would be really happy to have it on my system again. Till then I guess I will have to miss gwibber!

---

### Post by bredman on 2010-05-07
I had to abandon Gwibber because it will not work through a proxy. Moved to pidgin instead.

---

### Post by caixamagica on 2010-06-26
Not solved!

---

### Post by sukigenseki on 2010-06-26
Thanks to the person that suggested deleting the ~/.cache/gwibber folder because now it works for me once again! I only use it for facebook though, so I don't know if that would have helped for the other protocols...

---

### Post by relgames on 2010-09-01
gwibber is not working... pino is not working after the latest update... what else can be used as twitter client?

---

### Post by durand on 2010-09-01
I think gwibber will be updated soon with new code to get it working again, I'm not sure about pino because I think development is slowing down a bit there.

---

### Post by relgames on 2010-09-01
I managed to get gwibber working by updating to the latest version:

**$ sudo add-apt-repository ppa:gwibber-daily/ppa**
 **$ sudo apt-get update**
 **$ sudo apt-get upgrade**

---

### Post by yellerKat on 2010-09-01
> **relgames said:**
> I managed to get gwibber working by updating to the latest version:

**$ sudo add-apt-repository ppa:gwibber-daily/ppa**
 **$ sudo apt-get update**
 **$ sudo apt-get upgrade**

Not for me:

```
** (gwibber:3292): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:3292): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:3292): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 67, in <module>
    client.Client()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 533, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 63, in __init__
    self.setup_ui()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 159, in setup_ui
    self.stream_view = view_class(self.model)
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 316, in __init__
    self.navigation.render()
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 282, in render
    streams=self.model.get_streams(),
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 78, in get_streams
    if not self.model_valid: self.refresh()
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 82, in refresh
    self.model = self.generate_streams()
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 87, in generate_streams
    transients = json.loads(self.streams.List())
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 649, in _message_cb
    (candidate_method, parent_method) = _method_lookup(self, method_name, interface_name)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 244, in _method_lookup
    raise UnknownMethodException('%s is not a valid method of interface %s' % (method_name, dbus_interface))
UnknownMethodException: org.freedesktop.DBus.Error.UnknownMethod: Unknown method: List is not a valid method of interface com.Gwibber.Streams

```

---

### Post by relgames on 2010-09-01
> **yellerKat said:**
> Not for me
I don't understand why they have included this terrible "application" into the official release. It's working for me now, but has some strange effects; for example, it doesn't notify about new messages (even about @replies).

I'll switch to Pino as soon as version 0.3 is out - current one doesn't support OAuth...

---

### Post by Dan Lyke on 2010-09-01
So the solution appears to be that you need to restart DBus. I did that by rebooting.

Now if I can just get Gwibber to actually add a Facebook account... Sigh.

---

### Post by siddharthshetty on 2010-09-01
> **vivek40 said:**
> Bump!!!! guys someone please help... gwibber just does not work.. i can add my account through "Broadcast accounts" .. but after that when i open gwibber there is nothing there.. no tweets nothing

Gwibber is one of my favorites but there are many better twitter aps available on ubuntu like my personal favorite qwit which is fast and pretty cool.

well follow me on twitter --->[click here]("http://twitter.com/siddharthRON")<---

and where in INDIA do you live buddy ...i am from mumbai :)

---

### Post by shadow of the locust on 2010-09-02
> **relgames said:**
> I managed to get gwibber working by updating to the latest version:

**$ sudo add-apt-repository ppa:gwibber-daily/ppa**
 **$ sudo apt-get update**
 **$ sudo apt-get upgrade**

this got gwibber updating again for me.

thank you =D>

---

### Post by Rickles65 on 2010-09-10
Tried all of the above - NO JOY.

I saw a CLI twitter client, might be worth a try. TTYtter...


Sadly, it looks like gwibber is dead. Sure there's active development but obviously no testing.

---

### Post by t3h_g3n3r4l on 2010-09-12
try using your facebook account name instead of email address for the login.  I tried that in conjunction with deleting the ~/.cache/gwibber folder and was finally able to add facebook.

---

### Post by boelectronic on 2010-11-01
My problem is that I cannot add (authorize) any account, need to set proxy for that, but I could not find a way to do

---

### Post by Midway on 2010-11-03
> **t3h_g3n3r4l said:**
> try using your facebook account name instead of email address for the login.  I tried that in conjunction with deleting the ~/.cache/gwibber folder and was finally able to add facebook.

Thanks neighbor!  I finally got Facebook and Twitter working here :)

---

