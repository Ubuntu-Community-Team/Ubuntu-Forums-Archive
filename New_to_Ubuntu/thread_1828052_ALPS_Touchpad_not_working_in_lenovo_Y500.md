---
title: "ALPS Touchpad not working in lenovo Y500"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by hishamhusain on 2011-08-18
Hi,

I am using ubuntu 11.04. My laptop has ALPS Touchpad. But it is not working.

I have run the command XINPUT --LIST and the result is 

hisham@LPT:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft  Microsoft Basic Optical Mouse v2.0 	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB 2.0 Camera                          	id=11	[slave  keyboard (3)]
    &#8627; Ideapad extra buttons                   	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]

Can anyone please help in fixing this issue.

Thanks in advance
Hisham

---

### Post by MarjaE on 2011-08-19
Yeah. It is a common issue across many different machines. There are no reliable drivers for the ALPS touchpad, and I keep trying to find a reliable way to disable the touchpad because it's worse when it's "working" and randomly moving the cursor and randomly selecting things than when it's not "working" at all.

---

