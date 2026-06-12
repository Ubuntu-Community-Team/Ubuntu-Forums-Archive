---
title: "Ubuntu just freezes on me!"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2009-03-15
Hello all!

I have a problem with my lovely OS :) Sometimes it just freezes on me.This happens when I use Internet Explorer for linux (ies4linux).I need this program because my brother uses to play pool on this site 
[www.gamedesire.com](www.gamedesire.com)
and I can't get it to work on any other browser.I've tried Firefox, Opera, Konqueror, Epiphany, Kazehakase and   no use...So I'm stuck using Internet Explorer. The troublle is that once in a while the system crashes:the screen grays out and it won't respond to any command except Alt PrtSc R E I S U B.Can someone tell me what to do to fix that? Do some of you play on this site?
Any ideas are most welcome!

---

### Post by Vadi on 2009-03-16
I think you should ask for help ie4linux people, they can help you better.

---

### Post by Troll_the_Great on 2009-03-16
> **Vadi said:**
> I think you should ask for help ie4linux people, they can help you better.

Great, but where do I find them?

---

### Post by .:Justus:. on 2009-03-16
> **Troll_the_Great said:**
> Great, but where do I find them?

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)
Took me two seconds in google^^

---

### Post by Troll_the_Great on 2009-03-16
> **.:Justus:. said:**
> [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)
Took me two seconds in google^^

Thanks for the page, but there's no forum there. Who should I ask (and how)?

---

### Post by .:Justus:. on 2009-03-16
> **Troll_the_Great said:**
> Thanks for the page, but there's no forum there. Who should I ask (and how)?

There is a blog, and it lists a couple bugs similar to your problem, you can also comment without signing up so i´d recommend you ask them on the blog.

---

### Post by Troll_the_Great on 2009-03-16
> **.:Justus:. said:**
> There is a blog, and it lists a couple bugs similar to your problem, you can also comment without signing up so i´d recommend you ask them on the blog.

I saw the blog, but I can't post.I click on "Skip to comment form" and nothing happens. I tried also creating an account, but I can't do that either. I have only the option to log in.So I'm out of ideas...:(

---

### Post by Troll_the_Great on 2009-03-18
Bump!

---

### Post by .:Justus:. on 2009-03-18
> **Troll_the_Great said:**
> I saw the blog, but I can't post.I click on "Skip to comment form" and nothing happens. I tried also creating an account, but I can't do that either. I have only the option to log in.So I'm out of ideas...:(

Man you´re right, how confusing is this site, it says that there´s an option to create an account but it´s no where in sight, neither is the comment form^^ sorry i can´t help you, you might have to scan google a bit for some answers.

Or you can email the guy who made it, [http://www.tatanka.com.br/ies4linux/page/User:S%C3%A9rgio_Lopes](http://www.tatanka.com.br/ies4linux/page/User:S%C3%A9rgio_Lopes)

---

### Post by Troll_the_Great on 2009-03-28
It happened again guys...I'm pretty desperate, I don't know what to do...:(:(:(

---

### Post by Ms_Angel_D on 2009-03-28
From what I understand ies4linux's development has kinda fell by the wayside. Have you tried firefox in wine. You can install it using [wine-doors]("http://wddb.wine-doors.org/").

---

### Post by andyswarbs on 2009-03-28
Hi, I just started using Ubuntu on a 7 yr old compaq presario.  It had a hanging problem as well.  I fixed my hanging very easily, and now it is perfectly stable (touch wood).  I had an associated problem that I was trying to connect to the web over a belkin FSD7010 pcmcia card - one that I knew worked perfectly well.

Anyway the fix that fixed the wifi and made ubuntu stable was  posted from [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

3.1.3. System locks upon card insertion
When a card is first inserted, the system attempts to read the card's
memory. This can sometimes cause your system to lock-up. Try this to
see if it helps:

1) Open the file /etc/pcmcia/config.opts
gksudo gedit /etc/pcmcia/config.opts

2) Find the following section:
 include memory 0xc0000-0xfffff
 include memory 0xa0000000-0xa0ffffff
 include memory 0x60000000-0x60ffffff

3) Change it to look like this:
 include memory 0xd0000-0xdffff
 include memory 0xc0000-0xcffff
 include memory 0xc8000-0xcffff
 include memory 0xd8000-0xdffff

---

### Post by Troll_the_Great on 2009-03-28
> **andyswarbs said:**
> Hi, I just started using Ubuntu on a 7 yr old compaq presario.  It had a hanging problem as well.  I fixed my hanging very easily, and now it is perfectly stable (touch wood).  I had an associated problem that I was trying to connect to the web over a belkin FSD7010 pcmcia card - one that I knew worked perfectly well.

Anyway the fix that fixed the wifi and made ubuntu stable was  posted from [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

3.1.3. System locks upon card insertion
When a card is first inserted, the system attempts to read the card's
memory. This can sometimes cause your system to lock-up. Try this to
see if it helps:

1) Open the file /etc/pcmcia/config.opts
gksudo gedit /etc/pcmcia/config.opts

2) Find the following section:
 include memory 0xc0000-0xfffff
 include memory 0xa0000000-0xa0ffffff
 include memory 0x60000000-0x60ffffff

3) Change it to look like this:
 include memory 0xd0000-0xdffff
 include memory 0xc0000-0xcffff
 include memory 0xc8000-0xcffff
 include memory 0xd8000-0xdffff


OK, I will try it, but I don't use a wireless card, so I don't know if it will work.

---

### Post by Troll_the_Great on 2009-03-28
> **MetalHellsAngel said:**
> From what I understand ies4linux's development has kinda fell by the wayside. Have you tried firefox in wine. You can install it using [wine-doors]("http://wddb.wine-doors.org/").

Thanks, it works! Only one question:I can't minimize it. I press the minimize button, firefox minimizes for a microsecond and then maximizes again.Is this normal?

---

### Post by Ms_Angel_D on 2009-03-28
I'm not sure I don't use Firefox in wine, maybe someone else will be able to answer you better than I

---

### Post by Troll_the_Great on 2009-03-29
> **MetalHellsAngel said:**
> I'm not sure I don't use Firefox in wine, maybe someone else will be able to answer you better than I

OK, thanks anyway for the idea. It doesn't bother me too much, but I would be pleased if I could make it work 100%. I will wait for other opinions.
Cheers!

---

### Post by Troll_the_Great on 2009-03-31
Bump!

---

### Post by Troll_the_Great on 2009-04-02
Bump!

---

### Post by presence1960 on 2009-04-02
> **Troll_the_Great said:**
> Hello all!

I have a problem with my lovely OS :) Sometimes it just freezes on me.This happens when I use Internet Explorer for linux (ies4linux).I need this program because my brother uses to play pool on this site 
[www.gamedesire.com](www.gamedesire.com)
and I can't get it to work on any other browser.I've tried Firefox, Opera, Konqueror, Epiphany, Kazehakase and   no use...So I'm stuck using Internet Explorer. The troublle is that once in a while the system crashes:the screen grays out and it won't respond to any command except Alt PrtSc R E I S U B.Can someone tell me what to do to fix that? Do some of you play on this site?
Any ideas are most welcome!

Did you try firefox extension User Agent Switcher. it lets you choose IE or Netscape in its options so it "tricks" the web site into thinking you are using IE. Give it a try and see how it works.

---

### Post by Troll_the_Great on 2009-04-02
> **presence1960 said:**
> Did you try firefox extension User Agent Switcher. it lets you choose IE or Netscape in its options so it "tricks" the web site into thinking you are using IE. Give it a try and see how it works.

OK, I've installed it, but how do I use it? I can't find the menu anywhere...:(

EDIT: I found it and it's not working. It's OK running in the windows firefox through wine, the only problem is with the windows not minimizing (I stated above). If somebody could help me with that issue I would be grateful.
Cheers!

---

### Post by presence1960 on 2009-04-02
> **Troll_the_Great said:**
> OK, I've installed it, but how do I use it? I can't find the menu anywhere...:(

From Firefox go to Tools > User Agent Switcher > make your choice

---

### Post by Troll_the_Great on 2009-04-04
> **presence1960 said:**
> From Firefox go to Tools > User Agent Switcher > make your choice

I did that but it doesn't work (I've edited my previous post). I would like to know if I have to set up wine somehow, so firefox would be fully functional.
Cheers!

---

### Post by Net_Resident on 2009-04-04
You probably already tried this but does [IEtab for Firefox]("http://addons.mozilla.org/en-US/firefox/addon/1419") work for what you want?

---

### Post by Troll_the_Great on 2009-04-04
> **Net_Resident said:**
> You probably already tried this but does [IEtab for Firefox]("http://addons.mozilla.org/en-US/firefox/addon/1419") work for what you want?

IEtab for Firefox is not available for linux...:(

---

### Post by Net_Resident on 2009-04-04
Doh, sorry, I remembered the extension but didn't read their statement on it. Well free bump, maybe someone will have an answer for you. :)

---

### Post by Troll_the_Great on 2009-04-06
Bump!

---

### Post by Troll_the_Great on 2009-04-07
Bump!

---

### Post by Troll_the_Great on 2009-04-11
OK, I kind of sorted it...I installed an older version of wine and with it it works.Is this normal? Shouldn't it be compatible with all the versions of wine, especially with the newer ones?

---

### Post by Troll_the_Great on 2009-04-13
Bump!

---

### Post by Troll_the_Great on 2009-04-14
Bump!

---

### Post by achase79 on 2009-04-14
Sometimes there are regressions in the code at wine.  The best way to find the best version is to use the appdb.winehq.org website to see what verion of wine works or if there are any known workarounds or problems.

---

### Post by achase79 on 2009-04-14
you can also use winetricks ([http://wiki.winehq.org/winetricks]("http://wiki.winehq.org/winetricks")) to get ie6 and other items to make your wine capabilities more robust.

---

