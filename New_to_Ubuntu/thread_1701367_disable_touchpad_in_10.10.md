---
title: "disable touchpad in 10.10"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by bob brazie on 2011-03-06
I did a search and was more confused with what I found. <g>

I need to turn off the touch-pad on my new HP Pavilion dv7. It is a location that I seem to rub across it as I type. I use a mouse and not the touch-pad.

Is there maybe a setting in the configuration editor or may a add on such as compizConfig settings manager?

bob@bob-HP-Pavilion-dv7-Notebook-PC:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Wireless Optical Mouse® 1.00	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=15	[slave  keyboard (3)]
bob@bob-HP-Pavilion-dv7-Notebook-PC:~$ xinput list | grep -i touchpad
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
bob@bob-HP-Pavilion-dv7-Notebook-PC:~$ 

Thanks for any help. Bob.

---

