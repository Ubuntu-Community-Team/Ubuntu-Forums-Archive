---
title: "mIRC and Xchat help"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by john wagner on 2011-06-29
Hi again!  I just upgraded from Ubuntu 7.04 to 10.04 and now have a problem.  I use mIRC a lot, not to chat either.  

I am homebound and cannot hold a book for long (very painful), thus I read on my laptop.  Therein is my problem.  I buy a ton of ebooks each year, but not everything is available for sale (and yes, I use the online libraries also).  Thus I use the ebook channel on mIRC to download the books that  others have scanned and uploaded.  

It makes my homebound prison bearable.  I downloaded Xchat, but do not see a comparable site, just people talking.  

Does me no good.  

I tried to install mIRC using Wine, but my 10.04 has a conniption and claims I have to change my preferences (.exe being suddenly the anti-christ).  I've read the procedure and do not understand it enough to go ahead and try it.

How do I get my mIRC to work? Or, is there another book loaded site that I can download from?

Before you all scream about copyrights and theft, I am HOMEBOUND!  I have not left this house except via ambulance in 2 years.  I buy books when available, but...  All the older books (10years and more) are NOT available anywhere (except used bookstores as dead trees and I cannot hold them for longer than 1-2 minutes).  I am not selling them, I am reading them to make my house less of a prison.

---

### Post by Ozymandias_117 on 2011-06-29
If you remember the server that you were connecting to in mIRC, or if you are able to find out, you can simply join the same one in Xchat. ;P

---

### Post by john wagner on 2011-06-29
> **Ozymandias_117 said:**
> If you remember the server that you were connecting to in mIRC, or if you are able to find out, you can simply join the same one in Xchat. ;P

It's not listed tho...  Do I simply type it in?

---

### Post by jtarin on 2011-06-29
[Here's some help.]("http://puttscribe.com/faq/index.html")
ans also a [setup using mIRC,]("http://www.calvinshub.com/2008/11/how-to-download-e-books-from-mirc/") which might be helpful with some xchat configs.

---

### Post by john wagner on 2011-06-29
> **jtarin said:**
> [Here's some help.]("http://puttscribe.com/faq/index.html")
ans also a [setup using mIRC,]("http://www.calvinshub.com/2008/11/how-to-download-e-books-from-mirc/") which might be helpful with some xchat configs.

I don't see Xchat anywhere...  A lot of mIRC, which I know how to use.  I just need to know how to install it on ubuntu 10.04 or get Xchat to connect to it.

---

### Post by jtarin on 2011-06-29
> **john wagner said:**
> I don't see Xchat anywhere...  A lot of mIRC, which I know how to use.  I just need to know how to install it on ubuntu 10.04 or get Xchat to connect to it.If you know how to use mIRC you should be able to setup xchat.I only provided links to help you if you could not remember how to connect to the server. If you need an xchat-ebook walk-through.....sorry can't help you.

---

### Post by Ozymandias_117 on 2011-06-29
> **john wagner said:**
> It's not listed tho...  Do I simply type it in?

Yeah. Just type ```
/server irc.servername.com
``` then ```
/join #channel
```

---

### Post by john wagner on 2011-06-30
> **Ozymandias_117 said:**
> Yeah. Just type ```
/server irc.servername.com
``` then ```
/join #channel
```

In Xchat Add Servers or in Terminal?

---

### Post by Chronon on 2011-06-30
mIRC and Xchat are both IRC clients.  They can connect to the same servers and join the same chatrooms (channels).  

The commands posted by Ozymandias are IRC commands.  You simply type them into the status window (or any other chat window).  If you know the name of the server you can also add it via "add servers".

---

### Post by john wagner on 2011-07-01
> **Chronon said:**
> mIRC and Xchat are both IRC clients.  They can connect to the same servers and join the same chatrooms (channels).  

The commands posted by Ozymandias are IRC commands.  You simply type them into the status window (or any other chat window).  If you know the name of the server you can also add it via "add servers".

Awesome!  Works GREAT!  I just typed it into channnel ad wham bam thank you Ozymandious!
Thank you!

---

### Post by john wagner on 2011-07-01
> **john wagner said:**
> Awesome!  Works GREAT!  I just typed it into channnel ad wham bam thank you Ozymandious!
Thank you!

And Chronon (as well as all the others) too!

---

### Post by jtarin on 2011-07-01
I'm curious...did mIRC come preinstalled on your computer with the e-book server pre-configured?

---

### Post by john wagner on 2011-07-03
> **jtarin said:**
> I'm curious...did mIRC come preinstalled on your computer with the e-book server pre-configured?

No.  When I ran Dapper, I had mIRC installed through wine.  No problem at all.  10.04 argues with me at every *.exe I try to install via Wine.  Thus my frustration.  For Xchat I got it via the repositories and use the /server irc.irchighway.net command followed by /join #ebooks and blammo, there I am.  Easy!
Thanks everyone!

---

### Post by jtarin on 2011-07-03
The reason I ask is that at one point with mIRC you needed to enter the same information to connect. IRC clients all connect the same way.

---

### Post by john wagner on 2011-07-06
> **jtarin said:**
> The reason I ask is that at one point with mIRC you needed to enter the same information to connect. IRC clients all connect the same way.

Only on my initial setup on Dapper.  That was the only time I had to specify the server as well as the channel I wanted.  On Xchat, I have too specify the server as well as the channel each time I log on.  One extra step, eh.  Easy peasy, I LIKE Xchat, the layout, tools and such are better than the ones in mIRC.

---

### Post by jtarin on 2011-07-06
> **john wagner said:**
>  On Xchat, I have too specify the server as well as the channel each time I log on.  One extra step, eh. 
How do I autoconnect and join a channel when X-Chat loads?

In the Server list, select the Network you want to auto-connect to, click Edit and turn ON the "Auto connect to this network at startup" checkbox.

---

### Post by Chronon on 2011-07-06
You can configure Xchat so that it remembers that server too.

---

### Post by jtarin on 2011-07-06
You should post instructions for the OP to know how to do this.

---

### Post by Chronon on 2011-07-06
Well, I don't have xchat installed, but the process is pretty similar for most IRC clients.  Just look for an option to "Add server" or similar and fill in the relevant information.  

In Quassel (the IRC client that comes with Kubuntu) I go to File > Networks > Configure Networks.  Then fill in the host name of the server I want to add.

A quick google search leads me to believe that in xchat you should click the "networks" tab, then click "Add".

---

### Post by ixtok on 2011-07-07
I too get ebooks off IRC chat. I found the easiest chat client to use was chatzilla which is a firefox add on. Just go to "tools" in firerox, "add-ons" and lood for chatzilla. I use the #bookz channel on the undernet.

---

