---
title: "How to get Handbrake 0.9.3?"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by leinad177 on 2010-03-12
**EDIT: This thread is now about finding a good program which can rip dvds into AVIs for Ubuntu 9.10**

Can somebody please tell me how to get this?
i have no idea what a svn thing is...and i already googled for older versions but i couldnt find any for linux and i think i accidentally deleted my windows installer for it

> **Old Versions** 
 Older versions are only available in source code form from this site. You can check out any revision of code from our SVN repository. See the Development page for details. 

Alternatively, you can google for 3rd party sites that still host old builds. Sites such as VideoHelp or Oldmacapps are good places to look.this is the development page
[http://trac.handbrake.fr/wiki/Development](http://trac.handbrake.fr/wiki/Development)

any help is appreciated

---

### Post by underquark on 2010-03-12
[http://old.getdeb.net/app/HandBrake](http://old.getdeb.net/app/HandBrake)

Darn it.  Just checked that link and they've removed it with 0.9.4 being the oldest version I could find.

---

### Post by leinad177 on 2010-03-12
anyone else got any ideas?

---

### Post by coffeecat on 2010-03-12
> **leinad177 said:**
> anyone else got any ideas?

I kept the debs for both the amd64 and i386 versions of Handbrake 0.9.3. I thought they might come in useful! :) I've uploaded them to a private url where you'll be able to download them by ftp. (Warning - it's a slow server. You'll only get 30 kB/sec or so.) As soon as I've posted this, I'll pm you with the url. I'll leave them up for 24 hours only.

I can't leave them up for others to download - I don't have the bandwidth. So if anyone else wants these debs, you'll have to post the details of a free ftp server that I can upload them to.

---

### Post by howefield on 2010-03-12
> **leinad177 said:**
> anyone else got any ideas?

[http://www.tucows.com/download.html?software_id=607246&t=2](http://www.tucows.com/download.html?software_id=607246&t=2)

---

### Post by leinad177 on 2010-03-12
> **coffeecat said:**
> I kept the debs for both the amd64 and i386 versions of Handbrake 0.9.3. I thought they might come in useful! :) I've uploaded them to a private url where you'll be able to download them by ftp. (Warning - it's a slow server. You'll only get 30 kB/sec or so.) As soon as I've posted this, I'll pm you with the url. I'll leave them up for 24 hours only.

I can't leave them up for others to download - I don't have the bandwidth. So if anyone else wants these debs, you'll have to post the details of a free ftp server that I can upload them to.


im downloading it now, it should be done in about half an hour (my net has been capped)

---

### Post by leinad177 on 2010-03-12
> Unable to create ghb.

Internal error. could not parse UI descriptionthats what comes up when i try to run the i386 version from coffecat

---

### Post by coffeecat on 2010-03-12
> **leinad177 said:**
> thats what comes up when i try to run the i386 version from coffecat

im downloading the amd64 version now

to be honest i have no idea what the difference is

I just remembered: Handbrake is compiled to use particular versions of libraries that change from one release of Ubuntu to the next. Handbrake 0.9.3 won't run in Karmic. You have to use Jaunty. And I would guess that 0.9.4 won't run in Jaunty, but I haven't tried this.

That was why I kept the 0.9.3 debs. That version supports AVI and Xvid, both of which have been removed from 0.9.4.

Are you using Karmic? That's could be the problem. I'm afraid you've got a stark choice. Either run 0.9.3 in Jaunty or use MP4/h264 or ffmpeg in 0.9.4 in Karmic. It's a real nuisance for me. My media player is happy with the 0.9.3 produced AVIs, but can't cope with the MP4 container. 

:sigh:

---

### Post by leinad177 on 2010-03-12
> **coffeecat said:**
> I just remembered: Handbrake is compiled to use particular versions of libraries that change from one release of Ubuntu to the next. Handbrake 0.9.3 won't run in Karmic. You have to use Jaunty. And I would guess that 0.9.4 won't run in Jaunty, but I haven't tried this.

That was why I kept the 0.9.3 debs. That version supports AVI and Xvid, both of which have been removed from 0.9.4.

Are you using Karmic? That's could be the problem. I'm afraid you've got a stark choice. Either run 0.9.3 in Jaunty or use MP4/h264 or ffmpeg in 0.9.4 in Karmic. It's a real nuisance for me. My media player is happy with the 0.9.3 produced AVIs, but can't cope with the MP4 container. 

:sigh:


hmm...well do you know another program which can do avis'? (thats why i wanted 9.3)

---

### Post by coffeecat on 2010-03-12
> **leinad177 said:**
> hmm...well do you know another program which can do avis'? (thats why i wanted 9.3)

What are you encoding from?

Have a look at avidemux.

But also try DeVeDe. This is primarily for creating DVDs (and very good it is too), but it will also create AVIs. When you first open it, choose the last option - DivX / MPEG-4 - which produces an AVI. That's for the Karmic version - the interface has changed (and improved) over the last few releases. 

Both are in the Ubuntu repositories.

---

### Post by leinad177 on 2010-03-12
> **coffeecat said:**
> What are you encoding from?


i have no idea what you meant by that...
also im running 9.10 (i dont know what its called)

---

### Post by coffeecat on 2010-03-12
> **leinad177 said:**
> i have no idea what you meant by that...

I should have been clearer. :p What I meant was: what are you trying to create AVIs from? Ripping DVDs? From recorded MPEGs? If you describe what you're trying to do it's easier to advise the best software.

9.10 = Karmic Koala.

---

### Post by leinad177 on 2010-03-12
> **coffeecat said:**
> I should have been clearer. :p What I meant was: what are you trying to create AVIs from? Ripping DVDs? From recorded MPEGs? If you describe what you're trying to do it's easier to advise the best software.

9.10 = Karmic Koala.

im ripping dvds

---

### Post by coffeecat on 2010-03-12
> **leinad177 said:**
> im ripping dvds

Then have a look at k9copy. If they're encrypted DVDs, you'll need the libdvdcss2 package from [www.medibuntu.org](www.medibuntu.org) otherwise k9copy will crash. Also, make sure you have libdvdread4 installed. You can find that in the Ubuntu repositories.

I'm not sure whether it does AVIs. It will encode to MPEG-4 which I thought was a different container, but encoding to MPEG-4 in DeVeDe gives you an AVI. All these containers and codecs confuse me.

Anyway, give k9copy a try. It won't cost you anything!

---

### Post by leinad177 on 2010-03-12
ok thanks

---

