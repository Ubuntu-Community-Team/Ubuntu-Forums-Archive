---
title: "Playing .wvx files?"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by G-Com on 2009-11-11
I'm Catholic and I would like to watch some EWTN programming ([**LINK**](http://www.ewtn.com/audiovideo/index.asp)) on my laptop, but all their stuff is in the .wvx format.  It opens Movie Player and the status bar momentarily says "transferring from ewtn.edgeboss.net" and nothing happens.  I've tried downloading them and opening them in VLC and it still doesn't work.

Any ideas?

---

### Post by syntr on 2009-11-11
> **G-Com said:**
> I'm Catholic and I would like to watch some EWTN programming ([**LINK**](http://www.ewtn.com/audiovideo/index.asp)) on my laptop, but all their stuff is in the .wvx format.  It opens Movie Player and the status bar momentarily says "transferring from ewtn.edgeboss.net" and nothing happens.  I've tried downloading them and opening them in VLC and it still doesn't work.

Any ideas?

Try

gedit file.wxv

you should see a URL to a wmv file, then

wget url

now

open the file in Totem or use mplayer

---

### Post by G-Com on 2009-11-11
Didn't work.  It the first command line only opens gedit.

---

### Post by PRC09 on 2009-11-11
In 9.10 the first thing I add from Ubuntu Software Center is add/remove applications,close and then the old add/remove applications panel is available in System>Administration> Add/Remove applications.I find this easier than the new Ubuntu Software Center for adding multiple  applications so these are the applications I have added to make just about all media types play... Restricted Extras package,Totem and select Movie Player and Xine backend,gstreamer,add the ones that you can add except Fluendo.The streams from that site also come in Flash for some of them and I think Restricted extras installs that.Try that and post back.....

---

### Post by pjdallimore on 2009-11-12
As stated above... if you want to listen live to EWTN programming just go to the Radio site
[http://origin.ewtn.com/audiovideo/index.asp](http://origin.ewtn.com/audiovideo/index.asp)
select a Flash stream and it will work just fine (provided you have flash installed)

+pax christi

---

### Post by G-Com on 2009-11-14
> **PRC09 said:**
> In 9.10 the first thing I add from Ubuntu Software Center is add/remove applications,close and then the old add/remove applications panel is available in System>Administration> Add/Remove applications.I find this easier than the new Ubuntu Software Center for adding multiple  applications so these are the applications I have added to make just about all media types play... Restricted Extras package,Totem and select Movie Player and Xine backend,gstreamer,add the ones that you can add except Fluendo.The streams from that site also come in Flash for some of them and I think Restricted extras installs that.Try that and post back.....
I gave up.  Too complex.  Sorry, but I'm still relatively new to Linux.

However, I've found a solution: selecting a lower-quality stream.  100k vs. 300k.  It's not great, but still watchable.  So I won't complain.

Thanks and God bless all of you for your help. :)

---

### Post by G-Com on 2009-11-14
> **pjdallimore said:**
> As stated above... if you want to listen live to EWTN programming just go to the Radio site
[http://origin.ewtn.com/audiovideo/index.asp](http://origin.ewtn.com/audiovideo/index.asp)
select a Flash stream and it will work just fine (provided you have flash installed)

+pax christi
Thank you. :)

Pax Vobiscum! :)

---

