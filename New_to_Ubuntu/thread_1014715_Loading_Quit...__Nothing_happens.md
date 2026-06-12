---
title: "Loading Quit...  Nothing happens"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by th00ht on 2008-12-18
I like to shutdown my Ubuntu (8.04 on EeePC 901) installation occasionally. Yet when I click the Quit... button the response is varying. Sometimes I get the Logoff/Shutdown/reboot dialog, Something I only see "Loading  Quit..." sometimes nothing happens at all and I just keep the power button pressed for 4 seconds.

how can I improve the reliability of the "Quit..." button?

---

### Post by Michael.Godawski on 2008-12-18
> **th00ht said:**
> I like to shutdown my Ubuntu (8.04 on EeePC 901) installation occasionally. Yet when I click the Quit... button the response is varying. Sometimes I get the Logoff/Shutdown/reboot dialog, Something I only see "Loading  Quit..." sometimes nothing happens at all and I just keep the power button pressed for 4 seconds.

how can I improve the reliability of the "Quit..." button?

What do you mean you like to shutdown the installation?

What happens when you run in terminal this shutdown command:

```
sudo shutdown -h now
```

---

### Post by donkyhotay on 2008-12-18
> **th00ht said:**
> I like to shutdown my Ubuntu (8.04 on EeePC 901) installation occasionally. Yet when I click the Quit... button the response is varying. Sometimes I get the Logoff/Shutdown/reboot dialog, Something I only see "Loading  Quit..." sometimes nothing happens at all and I just keep the power button pressed for 4 seconds.

how can I improve the reliability of the "Quit..." button?

Yes, can you clarify this a little bit. It sounds to me as if the quit screen in gnome takes a long time to appear so that you can actually shutdown your system. Is this what you mean or do you mean after confirming shutdown that computer takes a long time to shutdown?

---

### Post by hailukah on 2008-12-18
Are you using ubuntu netbook-remix?  If so there is a problem with the quit button on the launcher.  The developers are working to resolve this issue but in the mean time when you click the Go Home button (ubuntu icon) you can use the exit button on the task bar.  It'll just let you log out but you can shutdown from GDM.

Another option is to right-click on the panel and go to 'Add to Panel' and add the shutdown button.

---

### Post by th00ht on 2008-12-19
Yes to hailukah and donkyhotay. That is what I mean.

Incidentely I've found out that the "delay" seems to deminish or disappear when I have the machine running for some time (+30min?).

What is confusing is that the "Quit..." button at least shows a dialog the "Exit" button does nothing. 

I will try your hint hailukah 

J

---

### Post by th00ht on 2009-02-04
HI hailukah , Nothing at all happens when I click the Exit button on the home screen.:p

---

### Post by th00ht on 2009-02-04
```
sudo shutdown -h now
```[/QUOTE]

obviously that will shutdown GNU/linux. But there is a button Quit... which is pretty useless if it doesn't work.

---

### Post by Eisenwinter on 2009-02-04
If you're really up for it, get yourself an icon, put it on a panel, and set it's command to sudo shutdown -Ph now.

---

