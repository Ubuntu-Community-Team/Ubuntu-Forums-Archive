---
title: "Updated to Ubuntu 9.10 and can't boot"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by jcojr72 on 2010-01-19
Hello,
I just upgraded to Ubuntu 9.10 and cannot boot.  If I let it boot normally I get to the screen with the Ubuntu logo, and then the computer just turns off.  So I try to get into the recovery area.  I have listed:
Ubuntu 9.10, kernel 2.6.31-17-generic
Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
Ubuntu 9.10, kernel 2.6.28-11-generic
Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
Ubuntu 9.10, memtest86+

If I choose the first recovery and then choose to boot normally, it says "Ubuntu 9.10 Jeremiah tty1" and asks for my login and password but this is in the terminal.  Then it says
"Last login:Tue Jan 19 19:57:21 EST 2010 on ttyl1
Linux Jeremiah 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
jeremiah@Jeremiah:~$"\

I have read that if the BIOS has the wrong time it may cause Ubuntu to have boot problems.  The battery on this laptop is so dead that anytime the cord is unplugged the laptop goes dead immediately.  COuld this have anything to do with this problem.  I have always had problems booting Ubuntu.

Thanks.

---

### Post by warfacegod on 2010-01-19
The battery of your laptop doesn't power the BIOS clock. I believe it's the cmos? battery. If your BIOS is no longer keeping the time then you need to change that battery not your main power cell. And yes, it is possible for a difference in system time and OS time to cause the behavior you're getting.

---

### Post by jcojr72 on 2010-01-19
Thanks warfacegod.  How can I work around this temporarily?  I tried resetting the BIOS date and time but still won't boot.  Thanks for the help.

---

### Post by lkraemer on 2010-01-20
jcocr72,
It appears as you have been dumped out to the Command Line Interface for
tty1.  What happens if you try CNTL ALT F7?  Will it switch you back
to the GUI?  If not, try typing the following in the CNTL ALT F1
Window:
```

startx

```
(F1 thru F6 are user tty?'s and F7 is the GUI)

[http://en.wikipedia.org/wiki/Table_of_keyboard_shortcuts](http://en.wikipedia.org/wiki/Table_of_keyboard_shortcuts)
(Last section)

lk

---

### Post by jcojr72 on 2010-01-20
Thanks lkraemer.  The startx command brought me into the GUI, but the mouse would not work.  I was able to get into the terminal and restart the computer from there succesfully.   Again I noticed the BIOS time was off again, I am guessing this is all cause by that.

Thanks.

---

### Post by lkraemer on 2010-01-20
Do you have the technical capability to open the laptop and change the
cmos battery?  I'd suggest having a service manual so you don't destroy
anything in that process!  Or, take it to someone who can change the
battery for you?  That shouldn't be too expensive.

Then you can proceed with playing with Ubuntu.

lk

---

### Post by warfacegod on 2010-01-20
Agreed. If you feel at all uncomfortable with electronics then take it to a computer specialist. Each type of laptop is different. Your CMOS battery could be just under an access panel or buried deep within. It depends entirely on how the laptop was assembled. I have a Toshiba Satellite P25-s607 that I took about 2/3 of the way apart and never even saw the CMOS battery.

My apologies for not replying sooner.

---

