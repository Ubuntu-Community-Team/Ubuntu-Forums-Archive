---
title: "Is it possible to downgrade versions?"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by LinuxFox on 2010-05-02
I have a question, is it possible to downgrade versions of Ubuntu?  The reason I ask is because I installed 10.04 on my mother's computer and she said it's not as fast as 8.04.  I know 8.04 end of life is next year, so I was wondering if it's ok to install 8.04 for her again, in the event she doesn't like 10.04.

Any answers would be great please.

By the way, her computer's specs are 2.0GHz AMD Athlon XP 2400+, with 512MB of RAM

---

### Post by Paqman on 2010-05-02
You'll have to reinstall if you want to go back to 8.04

---

### Post by madjr on 2010-05-02
nope

just install in **another partition** (like 10 to 15gb for her usage should be enough)

you will have both

if you like stick with it, if not then you can delete it


also there're many tweak guides you can use and get 10.04 up to speed

you can also try lubuntu (very fast) or xubuntu 10.04 , and keep the support

---

### Post by sadaruwan12 on 2010-05-02
> **Paqman said:**
> You'll have to reinstall if you want to go back to 8.04

Yes, Backup the home folder of your mothers account then reinstall the system from scratch.

Just wondering wht does your mother mean by slow ?

---

### Post by LinuxFox on 2010-05-02
> **sadaruwan12 said:**
> Yes, Backup the home folder of your mothers account then reinstall the system from scratch.

Just wondering wht does your mother mean by slow ?Pretty much surfing the internet, she kept saying it was going slow, even though it's not on my laptop.  Then again my laptop has 1 GB of RAM instead of 512 MB.

She mainly uses Firefox

By the way, I tried putting in the Xubuntu Desktop and saw no real difference in performance.  How do I remove the Xubuntu Desktop from 10.04?

---

### Post by Michl on 2010-05-02
There is an issue with ext3 and ext4 that can be
responsible for slowness.  It is discussed in the
release notes.  10.04 is also problematic with older
systems for other reasons.  I'm surprised that such
a distro is LTS when many people who had the previous
LTS won't be able to use 10.04.  Feels more like
MS thinking than linux thinking.  I just had to
'downgrade' to 9.04 because 10.04 had too many
problems on my Dell C610 laptop -- the main one
being that its wireless is screwy.

In any case, to 'downgrade' you have to do a clean
install of the older distro.  Since you have to do
a clean install, partition your disk into one for
/ and the other for /home.  There are directions
on psychocats/ubuntu.  Then when you reinstall,
the system goes into root, and you will format
that partition.  You mount /home, but don't format
it.  This is all quit clear when you hit manual
partition during reinstalling.

The advantage of this is that you don't have to
redo all the settings and reinstall all your 
personal folders and files after the reinstall.
For example, your bookmarks and mail settings
will all be there.

Hope this helps.  
M

---

### Post by sadaruwan12 on 2010-05-02
Xubuntu is a Desktop Environment you can use the synaptic to remove it and to install GNOME from the synaptic or from the command line interface.

Code:
```
sudo apt-get install GNOME
```

Well I don't think the net surfing depend that much on your PC hardware but I didn't noticed that kind of a slowness with FF.

If browsing speed is a problem for then try installing chromium instead of FF.

---

### Post by madjr on 2010-05-02
> **LinuxFox said:**
> Pretty much surfing the internet, she kept saying it was going slow, even though it's not on my laptop.  Then again my laptop has 1 GB of RAM instead of 512 MB.

She mainly uses Firefox

By the way, I tried putting in the Xubuntu Desktop and saw no real difference in performance.  How do I remove the Xubuntu Desktop from 10.04?

lubuntu is much faster and comes with chromium

---

### Post by madjr on 2010-05-02
> **Michl said:**
> There is an issue with ext3 and ext4 that can be
responsible for slowness.  It is discussed in the
release notes.  10.04 is also problematic with older
systems for other reasons.  I'm surprised that such
a distro is LTS when many people who had the previous
LTS won't be able to use 10.04.  Feels more like
MS thinking than linux thinking.  I just had to
'downgrade' to 9.04 because 10.04 had too many
problems on my Dell C610 laptop -- the main one
being that its wireless is screwy.

In any case, to 'downgrade' you have to do a clean
install of the older distro.  Since you have to do
a clean install, partition your disk into one for
/ and the other for /home.  There are directions
on psychocats/ubuntu.  Then when you reinstall,
the system goes into root, and you will format
that partition.  You mount /home, but don't format
it.  This is all quit clear when you hit manual
partition during reinstalling.

The advantage of this is that you don't have to
redo all the settings and reinstall all your 
personal folders and files after the reinstall.
For example, your bookmarks and mail settings
will all be there.

Hope this helps.  
M

maybe you can use another filesystem other than ext3 or ext4

but thats probably a kernel problem (just speculating)

---

### Post by LinuxFox on 2010-05-02
> **sadaruwan12 said:**
> Xubuntu is a Desktop Environment you can use the synaptic to remove it and to install GNOME from the synaptic or from the command line interface.

Code:
```
sudo apt-get install GNOME
```

Well I don't think the net surfing depend that much on your PC hardware but I didn't noticed that kind of a slowness with FF.

If browsing speed is a problem for then try installing chromium instead of FF.I could try that, but I don't know if she would go for it.  She's the type who "sets her ways" and doesn't like changing things.  I remember it took her a while to get used to Ubuntu, after switching from windows.  Personally I don't notice much difference in web browsing, though the start-up takes a while.

She's still gonna try 10.04 though, which reminds me.  She uses the numpad, and when she went to use it, it wouldn't work.  How do I fix this?  She got really annoyed when the numpad didn't work.

---

### Post by sadaruwan12 on 2010-05-02
> **Michl said:**
> There is an issue with ext3 and ext4 that can be
responsible for slowness.  It is discussed in the
release notes.  10.04 is also problematic with older
systems for other reasons.  I'm surprised that such
a distro is LTS when many people who had the previous
LTS won't be able to use 10.04.  Feels more like
MS thinking than linux thinking.  I just had to
'downgrade' to 9.04 because 10.04 had too many
problems on my Dell C610 laptop -- the main one
being that its wireless is screwy.

In any case, to 'downgrade' you have to do a clean
install of the older distro.  Since you have to do
a clean install, partition your disk into one for
/ and the other for /home.  There are directions
on psychocats/ubuntu.  Then when you reinstall,
the system goes into root, and you will format
that partition.  You mount /home, but don't format
it.  This is all quit clear when you hit manual
partition during reinstalling.

The advantage of this is that you don't have to
redo all the settings and reinstall all your 
personal folders and files after the reinstall.
For example, your bookmarks and mail settings
will all be there.

Hope this helps.  
M

EXT4 is relatively new so it's bound to have problems as they mentioned in the official release notes not everything gets stuck up in an EXT4 system but some packages these issues will get sorted out while the OS gets old every open source is like that thats why we have forums to let the developing people know what to do.

So no worries.

---

### Post by sadaruwan12 on 2010-05-02
> **LinuxFox said:**
> I could try that, but I don't know if she would go for it.  She's the type who "sets her ways" and doesn't like changing things.  I remember it took her a while to get used to Ubuntu, after switching from windows.  Personally I don't notice much difference in web browsing, though the start-up takes a while.

She's still gonna try 10.04 though, which reminds me.  She uses the numpad, and when she went to use it, it wouldn't work.  How do I fix this?  She got really annoyed when the numpad didn't work.

You've to turn it on in default it doesn't work in Ubuntu once you tern it on it stays like that you can turn it on from the NumLock button.

So what I see is your Mom have small changing problem you know some people doesn't like to change. Well I my experience with the new OS it's has the same kind of speed when it comes to the Internet.

I think she'll come around once she gets use to the new release and thats why it's named as the change. ;-)

---

### Post by sadaruwan12 on 2010-05-02
Yo Bro try these changes in your mother FF and to get to these settings type [COLOR="Red"]about:config[/COLOR] in your address bar and press enter. Then you'll see a warning press the button I'll be careful I swear.

Make Firefox Run Faster By Enabling Piplining:
Normally the browser will make one request to a web page at a time. When you enable pipelining, it will make several attempts at once, which really speeds up page loading. It's not very nice to slam websites with multiple requests. Be a good person and limit yourself to a reasonable number.
- Type network.http.pipelining into the filter bar
- Double click the network.http.pipelining entry to set the value to true
- Type network.http.proxy.pipelining into the filter bar
- Double click the network.http.proxy.pipelining entry to set the value to true
- Type network.http.pipelining.maxrequests into the filter bar
- Double click the network.http.pipelining.maxrequests entry and set the maxrequests to 15
- Right-click anywhere inside Firefox about:config page and select New-> Integer
- Name it nglayout.initialpaint.delay and set its value to 0 (zero)


Stop Firefox from Loading Pages in the Background:
Firefox downloads webpages from links it thinks you may click. This may make the experience seem faster but really it just bogs down Firefox and your netbook.
- Type network.prefetch-next into the filter bar
- Double click the network.prefetch-next entry to set it to false

---

### Post by egalvan on 2010-05-02
> **LinuxFox said:**
> Pretty much surfing the internet, she kept saying it was going slow, even though it's not on my laptop.
  Then again my **laptop has 1 GB of RAM instead of 512 MB.**

She mainly uses Firefox

Yes, you WILL see performance gains with upgrading her system to 1GB.
It will cost some cash, though Moms are worth it. Mother's Day is coming up anyway :)

For "cash-less" speed-ups...
There are "tweak"-type How-To's on the web that will help speed up Linux...
find one that is Lucid-specific... it will be easier.
Also look for FireFox "tweaks"... there is at least one that has stood the test of time.
Again, version-specific is easier (FF is at 3.6x on Lucid)

> I tried putting in the Xubuntu Desktop and saw no real difference in performance.
  How do I remove the Xubuntu Desktop from 10.04?

Removing the Xubuntu Desktop can be very messy.
Unless you are strapped for disk-space, I recommend leaving well enough alone.

Now if you did a separate Xubuntu install, that is totally different.
Then it's a matter of erasing the install, and up-dating GRUB.

---

### Post by jmszr on 2010-05-02
LinuxFox,

Here's a tutorial from Ubuntu Geek that should help with the Firefox speed problem: [http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html](http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html)

---

### Post by da burger on 2010-05-02
This page shows how to remove KDE of XFCE to get to GNOME. [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by LinuxFox on 2010-05-02
> **sadaruwan12 said:**
> Yo Bro try these changes in your mother FF and to get to these settings type [COLOR="Red"]about:config[/COLOR] in your address bar and press enter. Then you'll see a warning press the button I'll be careful I swear.

Make Firefox Run Faster By Enabling Piplining:
Normally the browser will make one request to a web page at a time. When you enable pipelining, it will make several attempts at once, which really speeds up page loading. It's not very nice to slam websites with multiple requests. Be a good person and limit yourself to a reasonable number.
- Type network.http.pipelining into the filter bar
- Double click the network.http.pipelining entry to set the value to true
- Type network.http.proxy.pipelining into the filter bar
- Double click the network.http.proxy.pipelining entry to set the value to true
- Type network.http.pipelining.maxrequests into the filter bar
- Double click the network.http.pipelining.maxrequests entry and set the maxrequests to 15
- Right-click anywhere inside Firefox about:config page and select New-> Integer
- Name it nglayout.initialpaint.delay and set its value to 0 (zero)


Stop Firefox from Loading Pages in the Background:
Firefox downloads webpages from links it thinks you may click. This may make the experience seem faster but really it just bogs down Firefox and your netbook.
- Type network.prefetch-next into the filter bar
- Double click the network.prefetch-next entry to set it to falseThanks, maybe I'll try this.  Though, I just installed Chomium on her computer and it runs faster.  Maybe she'll try it because it's faster.  She tried Ubuntu after I told her it can't get Windows viruses. :)

Thanks for the help guys, hopefully things will run smoothly with 10.04 on her computer.

---

### Post by chillicampari on 2010-05-02
> **LinuxFox said:**
> ...

She's still gonna try 10.04 though, which reminds me.  She uses the numpad, and when she went to use it, it wouldn't work.  How do I fix this?  She got really annoyed when the numpad didn't work.

numlockx should work for this (it's in the repositories).

---

### Post by LinuxFox on 2010-05-02
> **chillicampari said:**
> numlockx should work for this (it's in the repositories).Thanks, that really solved that problem.  She'll be glad to use it again.

---

