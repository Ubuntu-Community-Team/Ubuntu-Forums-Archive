---
title: "Wireless Connection"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by WizardofOgg on 2009-11-08
I am a Newbie.  I have installed Ubuntu 9-10 as a dual boot on my laptop.  When I am connected by ethernet cable to my router I have complete access to the internet.  However my wireless connection does not work.  If I go out of Ubuntu and into Windows Xp professional the wireless connection is just fine.  How can I correct this.  My internet provider is Telus and my router is a D-Link DI-524. If someone could advise I would appreciate simple language.  Thank you.

Stuart

---

### Post by dvlchd3 on 2009-11-08
Check System -> Administrator -> Hardware Drivers

You may have to activate a restricted driver.  These drivers are closed source, and therefore cannot be supported by Ubuntu.  If you need the functionality there is usually nothing wrong with activating them, so do not worry.

If you wireless card is not listed, post the output to the following command so we can see what wifi card you are using and possibly offer solutions from there:

```

lspci | grep Network

```

---

### Post by oldsoundguy on 2009-11-08
What card or chip is in the computer?

(IF you do not know, you can run "lshw" in the command window .. or if you want a permanent print out record of your hardware, open Windows and d/l and run Belarc Advisor.)

---

### Post by WizardofOgg on 2009-11-08
The chip is Intel(R)Pro/Wireless 2915 ABG according to Belarc

---

