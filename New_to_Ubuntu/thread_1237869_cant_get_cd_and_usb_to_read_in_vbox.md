---
title: "cant get cd and usb to read in vbox"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by misswham on 2009-08-11
I have successfully downloaded vbox, thanks to you all, but I have inserted my blackberry sync software into my cd drive and it does show up in my xp running in vbox but it wont totally come through.  it is in my computer and i double click it and it shows up in the toolbar at the bottom and the page starts but it stays blank.  it also is showing up on my ubuntu desktop.  I also inserted my external harddrive and it isnt recognizing it in vb XP but it too is showing up in ubuntu.

What can i do to correct this?

---

### Post by halitech on 2009-08-11
did you install virtualbox-ose (from the Ubuntu repo) or did you install Sun Virtualbox (from their website)?

---

### Post by misswham on 2009-08-11
from the website

---

### Post by halitech on 2009-08-11
ok good cause the virtualbox in the repo doesn't have usb support.

Open Virtual Box, do not start the VM yet. Select your VM and then look in the right pane and you should see USB. Does it say there are any active filters?

---

### Post by misswham on 2009-08-11
it says 0

---

### Post by halitech on 2009-08-11
ok, click on the usb and it will give you another window. Then click on Add (should be the second icon on the right) and select the usb drive from the list. The click okay. Now click on the cd/dvd drive. You want it to be on Mount CD/dvd drive and select host cd/dvd drive. Now when you start VB you should see both items.

---

### Post by misswham on 2009-08-11
Thank you.  My usb is showing 1 active but it still isnt reading my ext harddrive.  i do know that when i mount it, it shows up twice on my ubuntu desktop and it also is read in my full install of XP.  I think the cd part is working.  The software has started downloading but it is taking extremely long.  it appears to be stuck but i will give it a few mins.  

Any other ideas about the usb?

---

### Post by misswham on 2009-08-11
I have been tinkering with it and I added my external harddrive to the usb part of my vbox.  it did show up there but when i log onto windows in vbox it wont show up there.  I have 3 usb ports on front and i have tried in all of them.  Now when i hit devices at the bottom of the page, it shows up there but when i move the cursor over the usb icon it says none found and when i go to my computer in xp it isnt there. 

any ideas

---

### Post by nandemonai on 2009-08-11
Have you tried setting up a filter under the VM settings -> USB to filter the device down to vbox?

Also confirm you're in the vboxusers group (check Users and Groups).

---

### Post by misswham on 2009-08-11
I went to filters and it was on no but i changed it to any on all things listed in the usb section.  i hit ok and still it doesnt read anything i connect to any of the usbs.  i am sure it is a setting that has to be off that i am not getting.  this would be a dream come true if i could get this to work.  the cd is working fine it is just the usb.  also i went to user in admin and what am i supposed to be looking for and what am i supposed to do when i am there?

---

### Post by misswham on 2009-08-12
Almost got everything working.  Got the vbox usb to detect my external harddrive but now i cant get my blackberry to show up.  Can anyone help me with getting my blackberry to show up in XP on vbox?

---

### Post by halitech on 2009-08-12
take the same steps to add the blackberry to the usb filter list

---

### Post by misswham on 2010-02-28
Hi again.  I have a new pc now and I have readded virtualbox.  I am having a problem getting it to recognize my blackberry.  I have gone through the filters and activated them.  I have added my external harddrive and my flash drive and they both work fine.  I have dont my blackberry and it wont get recognized.  from the post above, I had this problem when I first downloaded VB last year but apparently I figured it out.  I dont remember what exactly I did last time but can someone give me some light on the situation.  i added it exactly the same way I did the other USBs and for some reason I cant figure it out.

PLEASE HELP

---

