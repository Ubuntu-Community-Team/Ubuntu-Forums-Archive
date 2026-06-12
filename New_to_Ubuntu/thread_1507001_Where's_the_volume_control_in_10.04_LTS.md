---
title: "Where's the volume control in 10.04 LTS"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by bobmac on 2010-06-11
I've managed to upgrade my laptop to 10.04 LTS. However, the volume control icon has disappeared and I can't locate it.

I've hunted around the taskbar thingy the new add/remove programs and the syn.. manager thing to no avail.

Can anyone help me find  it

---

### Post by Elfy on 2010-06-11
Install indicator-sound

---

### Post by rajeev1204 on 2010-06-11
> **bobmac said:**
> I've managed to upgrade my laptop to 10.04 LTS. However, the volume control icon has disappeared and I can't locate it.

I've hunted around the taskbar thingy the new add/remove programs and the syn.. manager thing to no avail.

Can anyone help me find  it


Right click on panel >add to panel > indicator applet

---

### Post by garvinrick4 on 2010-06-11
> **bobmac said:**
> I've managed to upgrade my laptop to 10.04 LTS. However, the volume control icon has disappeared and I can't locate it.

I've hunted around the taskbar thingy the new add/remove programs and the syn.. manager thing to no avail.

Can anyone help me find  it It is in the notification area (upper right hand) with network applet.

You can right click on little line hard to see to the left of notification area. Delete it.'
right click on panel  go to add to panel and select Notification Area and Add it. See if the sound
applet comes back.
 There is also a Sound in System/Preferences to Sound: Right click on it and add to panel.

You can also go into System/preference/Keyboard shortcuts and make sound up F12 and sound down F10 because F11 is full screen in you Movie player (plays videos)
 That works well on laptop to just have shortcut keys instead of moving pointer.

---

### Post by bobmac on 2010-06-11
Fantastic folks. It's fixed.

---

### Post by rajeev1204 on 2010-06-11
> **garvinrick4 said:**
> It is in the notification area (upper right hand) with network applet.

You can right click on little line hard to see to the left of notification area. Delete it.'
right click on panel  go to add to panel and select Notification Area and Add it. See if the sound
applet comes back.
 There is also a Sound in System/Preferences to Sound: Right click on it and add to panel.

You can also go into System/preference/Keyboard shortcuts and make sound up F12 and sound down F10 because F11 is full screen in you Movie player (plays videos)
 That works well on laptop to just have shortcut keys instead of moving pointer.


Hi garvin ,

The volume control has been moved into the indicator session applet from 10.04, it doesnt appear with the notification applet.

---

### Post by AnimalMagic on 2010-06-11
Is there anyway to remove the envelope icon? I don't use evolution and the icon just takes up space...

---

### Post by garvinrick4 on 2010-06-11
> **rajeev1204 said:**
> Hi garvin ,

The volume control has been moved into the indicator session applet from 10.04, it doesnt appear with the notification applet. Yes thanks for heads up, I just checked in maverick and it is where you say.

---

### Post by rajeev1204 on 2010-06-11
> **AnimalMagic said:**
> Is there anyway to remove the envelope icon? I don't use evolution and the icon just takes up space...


Hi , the envelope icon is not for evolution, its for chat, social and mail all together.

Its entirely meaningless / stupid , but until the next ubuntu release, it wont go away.Its been there for 2 releases now. You can probably use a different icon set which replaces that letter icon with some thing else.

I cant find such an icon set though so you have to search for it.

---

### Post by Elfy on 2010-06-11
> **AnimalMagic said:**
> Is there anyway to remove the envelope icon? I don't use evolution and the icon just takes up space...

If you want to remove it and have no use for the IM nor evolution indicator - remove 

```
indicator-me
```

---

### Post by AnimalMagic on 2010-06-11
Sorry, what is indicator-me? a command line command? If so, it wasn't found...:confused:

I want to keep the volume control, but lose the envelope icon...

---

### Post by Elfy on 2010-06-11
> **AnimalMagic said:**
> Sorry, what is indicator-me? a command line command? If so, it wasn't found...:confused:

I want to keep the volume control, but lose the envelope icon...

Sorry - either look in syanptic for it or do

```
sudo apt-get remove indicator-me
```

posibbly need to logout for it to take effect - be aware that applet is not just for e-mail - but empathy/pidgin etc

---

### Post by AnimalMagic on 2010-06-12
OK, I tried that, but the envelope remains :( I've also rebooted to make absolutely sure... It's not THAT important, just a minor irritant :-)

Sorry to OP for hijacking...

---

