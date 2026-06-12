---
title: "Is there a auto dialup disconnector for linux"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by skew on 2007-02-16
One program that I really miss from my Windows days was a small utility program called "disconnecter",
which automatically disconnected (hungup) the modem when a download was finished. I've looked everywhere I can think of online but can't find a Linux substitute for this handy program.

As a last ditch attempt I thought I'd make a plea to this forum. Maybe someone here knows of such a utility. Maybe a there is some script or program I can download that'll tell, for instance that there has been no traffic for a few minutes and then automatically hang up the connection?

Would be especially handy when using Synaptic to download updates overnight.

Anyone?

thanks,
Steve

---

### Post by apjone on 2007-02-16
Did you do your downloads via disconnecter?

---

### Post by skew on 2007-02-16
> **apjone said:**
> Did you do your downloads via disconnecter?


No. The Disconnector utility I used with windows gave you the choice to hang-up after a set period of time or when a window that was open closed. It was a seperate program and not a  download manager. As an example; In the firefox when downloading a file there is a small  progress window that opens and shows the progress of the download. When the download completed the window closed and the diconnector picked up on that event and hungup. It could target any window event to latch on to, users choice.

Stephen

---

### Post by apjone on 2007-02-16
Not sure, try freshmeat.net or you could right a script. Did you specify the file/window?

---

### Post by skew on 2007-02-16
> **apjone said:**
> Not sure, try freshmeat.net or you could right a script. Did you specify the file/window?

I tried searching freshmeat, no joy.   Apparently there was once a program there which may have been similar to the '*connectionmanager*' I used with windows but it's now  no longer available. All the links to it failed.:(    And yes the windows utility did allow you to specify which window to watch. 

As for writing a script, i'll have to first learn how to do that...:confused:

---

### Post by Matchless on 2007-02-17
I have used the download manager kget to do this in the past.

---

### Post by skew on 2007-02-18
> **Matchless said:**
> I have used the download manager kget to do this in the past.

Okay thanks, I'll check it out. 

Stephen

---

### Post by RandomJoe on 2007-02-18
I don't know of a way to arbitrarily set up a program to shut down a link as you describe, but back when I was on dialup I used 'diald' to handle my connection.  It is a dial-on-demand daemon that dials out whenever there is Internet traffic, then disconnects after a period of inactivity.  Makes things a little handier if you have a small network using the same dialup connection.

[http://diald.sourceforge.net/](http://diald.sourceforge.net/)

---

### Post by skew on 2007-02-19
> **RandomJoe said:**
> I don't know of a way to arbitrarily set up a program to shut down a link as you describe, but back when I was on dialup I used 'diald' to handle my connection.  It is a dial-on-demand daemon that dials out whenever there is Internet traffic, then disconnects after a period of inactivity.  Makes things a little handier if you have a small network using the same dialup connection.

[http://diald.sourceforge.net/](http://diald.sourceforge.net/)

Great, I'll look into that as well. Thanks  

I didn't have much luck with kget. It refused to disconnect after the download finished even though I set it to do so with *poff*, which works independently in the terminal. Go figure...
also  kget doesn't work with synaptic downloads.:(

---

### Post by BigDXLT on 2007-02-28
While it is not as slick as what you are looking for, personally, I use Scheduler, (I think that's its name, I'm off yonder on a windows machine at the moment) anyway, I found it in the repositories.  Basically you'll see words like cron and stuff associated with it, and all sorts of stuff I can't remember off the top of my head.  Nonetheless, I have it setup to automatically disconnect at 6am every day.  Mind you, I have unlimited dialup hours so I can waste time online in the middle of the night, but with dialup, chances are it's busy at those hours anyway.  :mad: 

Good luck!

---

