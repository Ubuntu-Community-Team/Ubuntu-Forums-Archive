---
title: "&quot;Networking&quot; GUI"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by Batmagoo on 2006-07-21
I am successfully using a 3com wireless 11a/b/g card to connect
to wireless networks in multiple locations... BUT...

Using the GUI (System->Administration->Networking) is proving
to be quite a challenge.

For one thing, the help files describe a previous version of
the GUI, so I'm armed only with my own intuition!

However, the main problem is that when I use "Create location"
for multiple locations, the ESSIDs seem to migrate from one
location to the other!

And, if I change the ESSID of a location, the change lasts only
for the one session, and the _old_ ESSID returns following even
a reboot!  That old one (that is no good any more) won't go away,
and there's no trace of the new one.

All right.  If there is no way to _EDIT_ a location, fine.
I'll just _delete_ it.  But... following "Delete current
location"...  Then, even if I reboot, and start the GUI again,
if I create a new location... the old info is "helpfully"
plugged into my location, including the old, worthless, ESSID.

Is the _card_ caching this info?  Why can't I change it?
Why does it save my _old_ ESSID, but not the new one?

The only thing that really seems to work is to delete _all_
locations, exit the GUI, and then "Create location".

The information obviously survives multiple reboots, so it
must be cached somewhere.  Is there a config file I can edit?
(I've been a unix sysadmin for years and years, since back
before we _had_ GUIs, so I am very comfortable with that approach.)

If you can shed any light on this, I will appreciate it.

---

### Post by PhrankDaChickenGeek on 2006-07-21
Search for a program called 'Network Manager' in your package manager. It is a lot easier to use on wireless networks.

See it's home page: [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

---

### Post by Batmagoo on 2006-07-21
Thanks, Phrank, that looks as if it could be quite nice, if I could ever get it configured properly, and get it working properly.

However...

After installing, it just:
     - disables my currently-working connection
     - reports "No network devices have been found"
so i manually restart the connection with "system->administration->networking" and network-manager still reports "No network devices have been found".

After a reboot, things are no better.

I'm unsure of how to force network-manager to see the connection.

I've never used dbus before, so it is probably my ignorance of that, which is causing my inability to properly use network-manager.

I can continue to use the manual method to connect, but what I would _REALLY_ like to know is where does the "system->administration->networking" GUI hold its configuration information, because its annoying behavior is to save _old_ ESSIDS, and "forget" the new ones, so that I have to

     - delete all locations.

     - create the location that I want to use.

So, if i can't find out where _those_ config files are, then
maybe I can find out where dbus's config files are, but either
way, it looks like i have a lot of reading to do, before I can ever stop performing the above work-around.



The docs and config files I have found so far are not of much help; I guess I'll keep nosing around for a while...

---

### Post by PhrankDaChickenGeek on 2006-07-21
Network manager will only see & manage interfaces that are not defined in /etc/network/interfaces (this is the file where the networking information is stored)

To fix this, go to 'System->Administration->Network Settings' and click on your wireless connection, select 'Properties' and uncheck 'Enable this Connection'.  Reboot, and you should be good to go!

---

### Post by Batmagoo on 2006-07-21
Thanks, Phrank,

> Network manager will only see & manage interfaces that are not defined in /etc/network/interfaces (this is the file where the networking information is stored)

Yes, I discovered that (just before I saw your reply!) by R'ing TFM:   <https://help.ubuntu.com/community/WifiDocs/NetworkManager> .

It also suggested that I had to relax the security in the dbus config files, which may or may not really have been necessary, but I did anyway, and it all works now!

Thanks for your help, and thanks for recommending network-manager; the interface is slick.

---

