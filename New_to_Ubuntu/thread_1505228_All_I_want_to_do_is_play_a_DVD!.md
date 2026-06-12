---
title: "All I want to do is play a DVD!"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by Badmonkey005 on 2010-06-08
[quote="Terminal"]dpkg: dependency problems prevent configuration of w32codecs:
 w32codecs depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
[/quote]

I've installed the restricted extras on top of VLC Media Player AND Kaffiene and nothing will play a DVD.

I looked around and found that some people had to install the w32 codecs and when I went to do that I got the error above. Problem is the version of libstdc I have is ABOVE that version yet it still won't work.

Can anyone help me out here? I want the end result to be me playing encrypted DVD's (regular store bought movies).

Thank you.

I have ubuntu 10.04

---

### Post by karthick87 on 2010-06-08
Install

```

sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3
```

---

### Post by Windows Nerd on 2010-06-08
Look [here]("http://ubuntuforums.org/showthread.php?t=766683&highlight=Multimedia+commands"). It is VERY easy to follow and straightfoward. I found it by that little searchbar you see in the top right. I kindly ask that you look there first (and then Google), as it is VERY likely that someone will have the same problem as you.

Scott

---

### Post by Badmonkey005 on 2010-06-08
E: Option apt-get: Configuration item specification must have an =<val>.

That's what was returned when I tried.

---

### Post by Windows Nerd on 2010-06-08
> **Badmonkey005 said:**
> E: Option apt-get: Configuration item specification must have an =<val>.

That's what was returned when I tried.
Tried what? I would love to help you, but if I don't know what you're talking about I (and others) get lost.

There is an entire DVD section (section 4 of 5) dedicated to DVD playback in that thread I linked.

---

### Post by Badmonkey005 on 2010-06-08
> **Windows Nerd said:**
> Look [here]("http://ubuntuforums.org/showthread.php?t=766683&highlight=Multimedia+commands"). It is VERY easy to follow and straightfoward. I found it by that little searchbar you see in the top right. I kindly ask that you look there first (and then Google), as it is VERY likely that someone will have the same problem as you.

Scott

I must apologize. I had seen the post beforehand but saw that it was outdated. I trust your judgement and the instructions on that page went flawlessly. Sorry for wasting your time and thank you very much for the reply.

---

### Post by Windows Nerd on 2010-06-08
> **Badmonkey005 said:**
> I must apologize. I had seen the post beforehand but saw that it was outdated. I trust your judgement and the instructions on that page went flawlessly. Sorry for wasting your time and thank you very much for the reply.
In all non-seriousness, is your problem solved?

Edit: And sorry for the semi-harsh way of telling you about the handy-dandy search bar/Google. I am helping you by not only telling you how to solve your problem, but also telling you how you can solve more problems in the future. Its sort of like the "Give a man a fish and you feed him for a day. Teach him how to fish and he can feed himself for a liftime" philosophy.

---

### Post by Metrop021 on 2010-06-08
ah i just had to go through this a minute ago, i ran through all the guides that google gave me but i had trouble actually opening the dvd. in case this applies to you: I had to navigate to the mounted dvd (in my case /media/DVD_VIDEO/) and open one of the .VOB files.

---

### Post by Badmonkey005 on 2010-06-08
> **Windows Nerd said:**
> In all non-seriousness, is your problem solved?

Yeah, figured I implied it when I said the instructions went flawlessly. Works perfect, thanks again.

---

### Post by Windows Nerd on 2010-06-08
> **Badmonkey005 said:**
> Yeah, figured I implied it when I said the instructions went flawlessly. Works perfect, thanks again.
Then you may mark this thread as solved. You can do that by using the "thread tools" thing-a-magig at the top of the thread by your very first post.

Welcome.

---

### Post by Nick_Jinn on 2010-06-08
> **Badmonkey005 said:**
> I've installed the restricted extras on top of VLC Media Player AND Kaffiene and nothing will play a DVD.

I looked around and found that some people had to install the w32 codecs and when I went to do that I got the error above. Problem is the version of libstdc I have is ABOVE that version yet it still won't work.

Can anyone help me out here? I want the end result to be me playing encrypted DVD's (regular store bought movies).

Thank you.

I have ubuntu 10.04



Just add Medibuntu. It will take care of all the codecs left out of restricted drivers.


Ubuntu should get with it and install all of them by default.

---

### Post by dineshs on 2010-06-09
Can you please try smplayer and tell result?

---

### Post by allegedlyyours on 2010-06-11
> **Windows Nerd said:**
> Look [here]("http://ubuntuforums.org/showthread.php?t=766683&highlight=Multimedia+commands"). It is VERY easy to follow and straightfoward. I found it by that little searchbar you see in the top right. I kindly ask that you look there first (and then Google), as it is VERY likely that someone will have the same problem as you.

Scott

I just wanted to say thanks for the re-direction to that page...the instructions were just what I needed. I was battling with the same issue for a few hours and had tried a few different fixes, but didn't happen to come across that particular page yet, so, thanks.

---

