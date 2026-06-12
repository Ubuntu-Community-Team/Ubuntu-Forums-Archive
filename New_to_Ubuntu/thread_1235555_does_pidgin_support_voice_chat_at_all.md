---
title: "does pidgin support voice chat at all?"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by heyyy on 2009-08-09
?

---

### Post by coldReactive on 2009-08-09
Nope, nor video chat.

And I like it like that.

Google **skype plugin for pidgin ubuntu** though.

---

### Post by heyyy on 2009-08-09
> **coldReactive said:**
> Nope, nor video chat.

And I like it like that.

Google **skype plugin for pidgin ubuntu** though.

im not asking about video...
i am asking about VoicE,like speaking through a microphone...

---

### Post by coldReactive on 2009-08-09
> **heyyy said:**
> im not asking about video...
i am asking about VoicE,like speaking through a microphone...

Skype is a voice client.

---

### Post by Tibuda on 2009-08-09
No, Pidgin does not support voice chat. [Skype]("http://www.skype.com") supports it, but it has its own protocol, so you won't be able to talk with your MSN or Yahoo friends using Skype. [aMSN]("apt:amsn") is a MSN client that supports voice. I'm not sure about other protocols... What protocol are you using?

---

### Post by pempem on 2009-08-10
that was also my problem. i just installed skype and it works well. cam and voice.

---

### Post by colau on 2009-08-16
> **heyyy said:**
> ?
No.
This is the problem with Pidgin.

---

### Post by colau on 2009-08-16
> **coldReactive said:**
> Nope, nor video chat.

And I like it like that.

Google **skype plugin for pidgin ubuntu** though.
I think, there is no ***"skype plugin/pugin for voice chat"*** for pidgin.

---

### Post by coldReactive on 2009-08-16
> **colau said:**
> I think, there is no ***"skype plugin/pugin for voice chat"*** for pidgin.

[http://eion.robbmob.com/](http://eion.robbmob.com/)

---

### Post by colau on 2009-08-16
> **coldReactive said:**
> [http://eion.robbmob.com/](http://eion.robbmob.com/)
Are you able to do voice chat with that plugin in pidgin?

---

### Post by kevdog on 2009-08-16
If you compile the mtn pidgin developmental branch -- vv (short for voice and video), it will work with voice only (not video yet) with XMPP (which is the protocol Jabber, Gmail, etc uses).  I'd provide more details but once I usually start about compiling from source, peoples' eyes start to glaze over.

---

### Post by mrbiggbrain on 2009-08-16
> **kevdog said:**
> If you compile the mtn pidgin developmental branch -- vv (short for voice and video), it will work with voice only (not video yet) with XMPP (which is the protocol Jabber, Gmail, etc uses).  I'd provide more details but once I usually start about compiling from source, peoples' eyes start to glaze over.

min light up :-) LFS already made me well aquainted to errors :-) still getting through that beast

---

### Post by khc on 2009-08-17
> **kevdog said:**
> If you compile the mtn pidgin developmental branch -- vv (short for voice and video), it will work with voice only (not video yet) with XMPP (which is the protocol Jabber, Gmail, etc uses).  I'd provide more details but once I usually start about compiling from source, peoples' eyes start to glaze over.

That's not really true, video should work too. I was able to view a Windows gmail (the in browser client, not gtalk) user's webcam, but had some encoding problem so the other end couldn't view mine. Pidgin-Pidgin video sessions should be more reliable.

Note that for jaunty, you will need libnice from karmic.

---

### Post by Yfrwlf on 2009-08-26
> **khc said:**
> That's not really true, video should work too. I was able to view a Windows gmail (the in browser client, not gtalk) user's webcam, but had some encoding problem so the other end couldn't view mine. Pidgin-Pidgin video sessions should be more reliable.

Note that for jaunty, you will need libnice from karmic.

I am using the Pidgin PPA for Jaunty.  Shouldn't it include all of the needed dependencies already?  Yet, voice and video options are grayed out for me.  I am using 2.6.1, and it says on their site that voice and video are supposed to be working now.

---

