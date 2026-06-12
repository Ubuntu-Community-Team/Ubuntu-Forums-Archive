---
title: "printer stopped   - maybe long story"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by cloyd on 2010-06-03
UNR 9.10
The basic problem is, mu Lexmark 2600 just stopped. When it first happened, I tried the troubleshooting tool said something to the effect that shared printers on servers, and to go to printing in system admin and mark "share printers." When I tried to print after that, still failed, and trouble shooting tool locked up.  I went back, and changed the system admin shared printer the way it was. Now still won't print, and troubleshooting tool  showing no printers connected. Then, one more screen to ask if it was a locally connect printer or a network printer. Here it locks (I can shut down the troubleshooting tool, but while it is running, it just shows the little spinning disc.

Now, here is the long story.

Gateway LT3103u
 
HID compliant mouse
 Synaptics PS/2 Port touchPad
 Generic PnP Monitor
 Atheros AR5B95 Wireless Network Adapter
 Reltek PCIe FE Family Controller
 AMD Athlon(tm) Processor L110
 Realtgek High Definition Audio
 Microsoft iSCISI Initator
 

 No windows on this machine. Lots of disc space. So, last night, I installed 10.4 side by side with 9.10.  Had seen a post on forum about cooling down CPU with 2.6.31.21 kernal on 10.4. (That is the same as I'm using in 9.04)  This has been the best for my wireless). I tried to install that kernel, and half-way succeeded.  It would boot, showing some errors, but 1) synaptic wouldn't work, and 2) wireless was poor. In addition, got an update screen that said some packages were incompletely installed. I would try running this, and it would fail  (tried two or three times.)

Ok. It wasn't time to switch to 10.4 yet. Use 9.04.  This morning everything worked fine. Then in 9.04, I got the same update screen that I got last night on 10.4, I think for the same kernal (32.22 i think.  Also, it said "distribution update".). I have trusted the updates . . .  for my first 6 months with Ubuntu, three have been no problems.  I went ahead. Everything seemed to work at the house. Picked up my computer and went to work, and printer problems.

This "update" did another thing that was strange. I had uninstalled rhythmbox. The update/upgrade reinstalled rhythmbox. No big deal, I just liked the simpler interface for my music in movie player. 

All of this long story may have nothing to do with the printer problem. Really, how could a 10.04 installation affect a 9.04 installation. It is just that  update that gets me. And, my last update on 9.04 was a few days ago, and there have been no problems and no messages.  

I really need my printer. It is essential to me.
Thanks

addendum:

as I was writing this message, trouble shooting tool finally came up with this. Said it could not solve problem, but offered this info.

                                 Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dests_available': [], 'cups_queue_listed': False}
Page 3 (Local or remote?):
{'printer_is_remote': False}
Page 4 (Choose device):
{'cups_device_attributes': {'device-class': u'direct',
                            'device-id': u'MFG:Lexmark;CMD:CPDNPA004;MODEL: 2600 Series;CLASS:Printer;DES:Lexmark 2600 Series;',
                            'device-info': u'Lexmark 2600 Series',
                            'device-make-and-model': u'Lexmark 2600 Series'},
 'cups_device_listed': True,
 'cups_device_uri': 'usb://Lexmark/2600%20Series'}
Page 5 (Locale issues):
{'printer_page_size': None,
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}

I know, printer problems are notorious. For as long as I have been using computers, printers have always been a problem.  It seems to be a problem in every OS. I wonder, has anyone written a book on making your printer work in Linux?

---

### Post by cariboo on 2010-06-03
It looks like cups isn't running, for Lucid (10.04) open a terminal and type:

```
sudo service cups start
```

For Karmic (9.10) and older type:

```
sudo /etc/init.d/cups start
```

---

### Post by cloyd on 2010-06-03
Thanks for the reply. I tried it in 9.10. Still no go. I'll try in 10.04.  10.04 won't print either. I have a HP at home, and I am wondering if it will print . . . Lexmark does seem to be a bit more tempermental. I will see after while. Meantime, I'll try you solution in Lucid.

---

### Post by cloyd on 2010-06-03
Well, those things didn't work, but I think the problem is solved, but I am not yet sure. I thought I'd try the solution in you suggested in Lucid.  Didn't work. But . . .

I asked Lucid to diagnose the problem. It told me I needed to change a print cartridge. 

Duh . . . shoulda known. It has happened before, but I had had no warnings that the cartridge was low. Lexmark prints so many then stops. Doesn't get lighter and lighter, it just stops. I think there is a counter and they print so many pages. Anyway, I didn't have another cartridge so I couldn't change it. 

But got home, tried my HP, and lo and behold, it worked!  Solved, and I will mark it so, and if the Lexmark won't work when I get a new cartridge, I may just retire it.  Thanks for taking the time. 

Sorry I didn't think. I should have.

---

