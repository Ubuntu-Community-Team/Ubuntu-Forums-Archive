---
title: "Difficulty printing to Dell 3010cn"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by Roadkill_aus on 2009-12-11
I have just set up Ubuntu 9.04 on a PC I built up out of various parts I had as a learning opportunity. As part of this I have attempted to st up the Dell 3010cn printer attached to the household network. When ever I try to print the printer brings up a message on its small LCD display stating "cancelling" and thats as close as I can get. This same PC when runng Vista will print to this Printer.

PC is consists of Intel® Desktop Board DQ965GF, Celeron D 3.46Ghz with 1 G or ram.

---

### Post by sandyd on 2009-12-11
lexmark printers are generally not supported.
however, there is a new post in the howtos section of the forum
p.s. just to stop confusion, Dell printers are actually rebranded lexmark printers.

---

### Post by Roadkill_aus on 2009-12-11
Thanks for that [carlee]("http://ubuntuforums.org/member.php?u=717412") i have had a start looking through the thread. 

Does anyone else know where I can access a translation table or look up which Lexmarc has been re branded to make it into a dell 3010cn?

---

### Post by ubushtu on 2009-12-12
I have the same situation with my 3010cn.  I installed the CUPS ppd from openprinting.org and see "Cancelling" on the printer LCD immediately after submitting a job.  It'll be nice if I can get this printer working.  It's the last hurdle in my Microsoft Windows separation :-)

I'll scour through the HowTo documentation as carlee recommended and report back if I find anything.

---

### Post by Roadkill_aus on 2009-12-12
Well now I am officially in over my head. While hunting around trying to find the correct lexmark model no I discovered this. [http://www.openprinting.org/show_driver.cgi?driver=pxldpl](http://www.openprinting.org/show_driver.cgi?driver=pxldpl) This could be an answer but I'm a little lost.

---

### Post by ubushtu on 2009-12-13
Hey thanks Roadkill_aus, the pxldpl driver appears to have worked for me!  I simply switched from the old pxlcolor driver that my 3010cn was configured for to this one and viola!  I'm running 9.10, here's what I did: 
[LEFT]
[LIST=1]
[*]Downloaded the pxldpl driver from openprinting.org
[*]System --> Administration --> Printers
[*]Right click 3010cn printer setup and choose 'Properties'
[*]Click 'Change' on the Make and Model
[*]Select the 'Provide PPD file radio button. Click 'Forward'
[/LIST]
Now whenever I submit a print job, the printer actually acknowledges the request instead of displaying 'Cancelling...'

I actually have a different issue now, unrelated to Ubuntu.  I see the familiar 004-332 error on the printer.  I've had to deal with this particular problem before on Windows.  

At any rate, I think the pxldpl driver did trick for me.
[/LEFT]

---

### Post by Roadkill_aus on 2009-12-15
Your are right Ubushtu I finally had a chance to look through it as well. The printer is now up running and happy.:P

So now its on to the next battle, my teenage kids have a list of things they want this PC to do. I suspect this includes running dedicated server packages for games they play on their PCs.  

Looks like I will have to be busy and learn quickly. :v{D>

---

