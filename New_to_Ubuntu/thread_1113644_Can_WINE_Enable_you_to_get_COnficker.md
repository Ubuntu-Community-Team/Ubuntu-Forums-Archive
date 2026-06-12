---
title: "Can WINE Enable you to get COnficker?"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by friyia@hotmail.com on 2009-04-01
hey guys just cause of that conficker thing out there I am getting some eery feelings can WINE enable you to have the codes windows has to install it?

---

### Post by llamabr on 2009-04-01
You could probably install it, but it wouldn't work.  If it's a virus it's probably an executable, but whatever it does next would not exist on your system.

Just to be safe, you could remove wine.  It's not very important, anyway.

---

### Post by friyia@hotmail.com on 2009-04-01
> **llamabr said:**
> You could probably install it, but it wouldn't work.  If it's a virus it's probably an executable, but whatever it does next would not exist on your system.

Just to be safe, you could remove wine.  It's not very important, anyway.

Ya I took wine off But I still Have wine Programs cause it's liek impossible yo take them off :@ :P but ya your right whatever it does to zombify my computer probably doesn't exist on my computer

Thanks man

---

### Post by linuxuser21 on 2009-04-01
No, Conficker is a worm.  Unless you have Wine continuously running & something such as Email, you should be good.

---

### Post by friyia@hotmail.com on 2009-04-01
> **linuxuser21 said:**
> No, Conficker is a worm.  Unless you have Wine continuously running something such as Email, you should be good.

how could wine run E-mail? :S  I used to use it for bitcomet

---

### Post by linuxuser21 on 2009-04-01
> **friyia@hotmail.com said:**
> how could wine run E-mail? :S  I used to use it for bitcomet

I mean for Thunderbird, Outlook express, ect.;)

---

### Post by friyia@hotmail.com on 2009-04-01
By the way how do you take off wine Programs?

---

### Post by llamabr on 2009-04-01
I've never used wine, but I think they all live in your ~/.wine/ dir.  If you've already deleted that, what other programs are there?

---

### Post by friyia@hotmail.com on 2009-04-01
By the way how do you remove wine Programs? I uninstalled wine and it didn't take them off

---

### Post by friyia@hotmail.com on 2009-04-01
> **llamabr said:**
> I've never used wine, but I think they all live in your ~/.wine/ dir.  If you've already deleted that, what other programs are there?

like Bitcomet
and Msn messanger

---

### Post by linuxuser21 on 2009-04-01
Even if you did get it via wine, it would only affect the contents within Wine and wouldn't start until you started using Wine.

---

### Post by friyia@hotmail.com on 2009-04-01
> **linuxuser21 said:**
> I mean for Thunderbird, Outlook express, ect.;)

oh okay

---

### Post by friyia@hotmail.com on 2009-04-01
> **linuxuser21 said:**
> Even if you did get it via wine, it would only affect the contents within Wine and wouldn't start until you started using Wine.

oh okay so it's not  gonna steal my personal information or anything
?

---

### Post by linuxuser21 on 2009-04-01
> **friyia@hotmail.com said:**
> oh okay so it's not  gonna steal my personal information or anything
?

No, you don't need to worry about anything :).  Even if it could, the file arrangements and types are different between Linux & Windows.  Besides, it hides itself as a Windows update.  How many of those do you have floating around?  ;)

---

### Post by friyia@hotmail.com on 2009-04-01
> **linuxuser21 said:**
> No, you don't need to worry about anything :).  Even if it could, the file arrangements and types are different between Linux & Windows.  Besides, it hides itself as a Windows update.  How many of those do you have floating around?  ;)

haha ya thanks man !!

---

### Post by linuxuser21 on 2009-04-01
No problem.

---

### Post by tracerbullet on 2009-04-01
> **linuxuser21 said:**
> Besides, it hides itself as a Windows update.

It does?

---

### Post by Bios Element on 2009-04-01
> **tracerbullet said:**
> It does?

Some versions yes.

---

### Post by linuxuser21 on 2009-04-01
> **tracerbullet said:**
> It does?

I read an article about how it comes as an update; however, I cannot find it.  It seems every story is different.  It's marked as a small virus, then, some places, it says it's absolutely terrible.  No one I know has got it; however, it's supposed to be everywhere.  Idk, any how, here is an article to read about it: [http://tech.yahoo.com/blogs/null/116396](http://tech.yahoo.com/blogs/null/116396).
Here is the McAfee info: [http://vil.nai.com/vil/content/v_153464.htm](http://vil.nai.com/vil/content/v_153464.htm)

---

### Post by linuxuser21 on 2009-04-01
Yes, it comes as an update as well.
Noton: [http://www.symantec.com/norton/theme.jsp?themeid=conficker_worm](http://www.symantec.com/norton/theme.jsp?themeid=conficker_worm)

---

### Post by tracerbullet on 2009-04-02
Right, I see. :)

---

### Post by mocoloco on 2009-04-02
> **friyia@hotmail.com said:**
> By the way how do you take off wine Programs?

Open your home folder, and show hidden files with "View -> Hidden files" (or Ctrl+H).
Delete the .wine folder.  That removes all of your fake windows files and settings, with the exception of two things that wine sets up natively, your menu items and mime types (if applicable).
Those items are in the .local folder. Look under ~/.local/share/applications/wine and also ~/.local/share/desktop-directores.
I don't have any wine apps that install mime types right now but I think those are found in ~/.local/share/mime or something similar. If not then you don't have any.

---

### Post by CBNorrie on 2009-04-04
I installed WINE and deliberately sought out sites said to be infected, not quite as easy as it sounds for very few reports tell you how deliberately to get infected.

Eventually I picked up a infection and have no real use for WINE deleted the application and any folders with WINE in the path.

No harm was done, ad none really could have bee beyond the infected account.

Charles Norrie

---

### Post by wllmtn on 2009-04-04
I found this site that can help anyone easily identify if they have the conflicker virus. 

[http://www.joestewart.org/cfeyechart.html]("http://www.joestewart.org/cfeyechart.html")

---

### Post by SunnyRabbiera on 2009-04-04
Wine is capible of getting viruses, and there are even some who infect wine on purpose to see how bad a virus really is.
But honestly wine wont effect the whole system, at best it could possibly do some harm to your home directory but most of the time they are rendered helpless under linux.

---

### Post by mocoloco on 2009-04-04
Honestly though affecting your home folder is much worse than just damaging some system files.  I can reinstall a broken system, it's my personal stuff that's irreplaceable.
I've been thinking about this though, because there seems to be a false sense of security when using wine, or a virtual machine, that they're like contained in their own environment. That's only true if you don't have a link from wine to your root file system (which is setup by default as drive Z), or in a VM, if you don't have shared folders mounted in your windows (which most people do, or at least I do to make moving files easier).
Depending on a user's habits that can be just as scary, especially in a VM since it should run a virus perfectly.
I suppose with viruses it's actually a good thing that Wine's not yet a perfect replacement for the win API :)

---

