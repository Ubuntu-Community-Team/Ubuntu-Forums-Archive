---
title: "More connection help needed"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by pj_kare on 2009-09-02
OK ... we sucessfully installed Feisty, installed gnome-ppp, no issues. Connected to internet, no problems. Couldn't update video driver (nvidia - screen resolution problem). Unable to update anything because support no longer available. So ... we have Jaunty disc, we'll upgrade - nope, need alternate disc for that. Ok, removed Feisty, clean install of Jaunty. Successfully installed video drivers. Finally got gnome-ppp install problems sorted - thanks to another thread and helpful replies - still can't connect, chap/pap permission errors.
Used 

sudo chmod a+rw /etc/ppp/ chap-secrets

and

sudo chmod a+rw etc/ppp/pap-secrets

that fixed permission errors. Now we almost connect - as soon as ISP answers it disconnects. No errors, checked Firefox for offline/online .... we can connect through Network-Admin, but it's dead ... connected, can't get email, browse, nothing happens ..

help ... please ... anyone ... 

We only have dialup access (bad dialup to boot ...) and have to use an external Netcomm/Banksia wave SP56 to connect ( We are yet to wrestle the winmodems into submission).

We really really really want to give ubuntu/linux a go but after a week of wrangling we are starting to lose heart. We were told ubuntu was the best to use because of its ease for newbies ... we are not getting that warm fuzzy non-windows feeling yet ... 

Apologies for length, but its part request, whine, rant, etc ..... :)

---

### Post by t0p on 2009-09-02
I suggest you try the program **wvdial**.  Unfortunately I think it might no longer be included in the Jaunty release.  You can find out if it's included by typing into the terminal

```
which wvdial
```

If you get a response like

```
/usr/bin/wvdial
```

it's there.  If you just get the bash prompt, it ain't there.

If you have internet access with another computer, you can download wvdial from [packages.ubuntu.com]("http://packages.ubuntu.com").  It's a pretty basic program so hopefully there won't be any dependencies needed to install it.

Let us know if you have/can get it.

---

### Post by pj_kare on 2009-09-02
We have wvdial installed, it's part of the gnome-ppp package.

---

### Post by pj_kare on 2009-09-02
**Finally solved it...if not by accident. **[COLOR=Red]**Not all steps below may have been needed.**[/COLOR]

Installed all dependencies for gnome-ppp except gnome-network-admin (not needed)

Installed gnome-ppp

set up pppconfig -> sudo pppconfig 
(selected Chap)

setup gnome-ppp

setup wvdial.conf -> sudo gedit /etc/wvdial.conf

change pppd permissions: ( the last entry was the one that finally got connection to work.)

sudo chmod +s /usr/sbin/pppd

sudo chmod a+rw /usr/sbin/pppd

sudo chmod a+x /usr/sbin/pppd

sudo adduser *myusername* dip ( just another tip found online )

Thought we did OK for 3-4 day old newbies.\\:D/

---

### Post by kevinatkins on 2009-09-02
Know what? BIG UP to you guys - not only have you solved your problem, but you've taken the time to come back here and tell us what you did...

---

