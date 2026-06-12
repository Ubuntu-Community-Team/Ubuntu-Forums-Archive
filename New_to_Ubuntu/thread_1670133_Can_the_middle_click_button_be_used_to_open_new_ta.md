---
title: "Can the middle click button be used to open new tabs in Firefox?"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by RichieB07 on 2011-01-18
From switching over to Windows I noticed that when I middle click on a link in Firefox, nothing happens.  Is there any way that it can be set up so that it'll open a new tab?

I went through the preferences and did not find any option to allow this.  I find this kind of frustrating as it's a lot easier than right clicking and selecting "Open in a New Tab".

Thanks for any help!

---

### Post by PaulHA2 on 2011-01-18
I opened up the tab on which I am writing this reply by clicking the middle button on my mouse. I'm on a Ubuntu machine. So, yes--and I did nothing special to set this up, so I presume it's the default. A hardware problem on your end, maybe?

---

### Post by RichieB07 on 2011-01-18
Do you know how to enable that though?  That's my question really.

---

### Post by Vaphell on 2011-01-18
middleclick to open/close tabs definitely works.

in the address bar type about:config, filter with 'middle' to get middleclick related settings
browser.tabs.opentabfor.middleclick should be the one you need, if it's false, change it to true

---

### Post by RichieB07 on 2011-01-18
Do you know how to enable that though?  That's my question really.

---

### Post by tobier on 2011-01-18
> **RichieB07 said:**
> From switching over to Windows I noticed that when I middle click on a link in Firefox, nothing happens.  Is there any way that it can be set up so that it'll open a new tab?

I went through the preferences and did not find any option to allow this.  I find this kind of frustrating as it's a lot easier than right clicking and selecting "Open in a New Tab".

Thanks for any help!

Does the middle mouse button work as intended in other applications? It might just be so that the middle button is mapped no nothing.

You can check that by opening a terminal, and typing:

```
$ xinput list
```

Look for a something that seems like a mouse in that list. For example, my output is:

```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Webcam                                  	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

```

Look up the id associated for you mouse (for me, it's 12), then monitor that device using xinput, like so:

```
$ xinput test mouse-id
```

Then press the middle mouse button. If the output does not indicate that you pressed the button, then the button mapping is not properly set up.

---

### Post by RichieB07 on 2011-01-18
> **tobier said:**
> Does the middle mouse button work as intended in other applications? It might just be so that the middle button is mapped no nothing.

You can check that by opening a terminal, and typing:

```
$ xinput list
```Look for a something that seems like a mouse in that list. For example, my output is:

```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Webcam                                      id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

```Look up the id associated for you mouse (for me, it's 12), then monitor that device using xinput, like so:

```
$ xinput test mouse-id
```Then press the middle mouse button. If the output does not indicate that you pressed the button, then the button mapping is not properly set up.

I can scroll with it in Firefox, but I can't click with it.  I tried what you said and it didn't do anything in terminal, so like you said the mapping must not be set up.  Any idea how to do this?

I have an Acer Aspire 5520 with a built-in mousepad if that helps at all.  Also running 10.10.

---

### Post by RichieB07 on 2011-01-18
Just an update, I ran that xinput test, but instead of doing the mouse I ran number 13, which was AlpsPS/2 Alps Glidepoint (Alps is the manufacturer for the drivers for my trackpad), and all the buttons worked, even the middle click button.

So now that it is configured, and I have Firefox's about:config set up correctly, why isn't this working yet?

---

### Post by tobier on 2011-01-18
> **RichieB07 said:**
> Just an update, I ran that xinput test, but instead of doing the mouse I ran number 13, which was AlpsPS/2 Alps Glidepoint (Alps is the manufacturer for the drivers for my trackpad), and all the buttons worked, even the middle click button.

So now that it is configured, and I have Firefox's about:config set up correctly, why isn't this working yet?

In that case, I have no idea why it wouldn't work. It works for me, and I don't even have a middle mouse button (I simulate one with clicking left+right on the touchpad at the same time).

---

### Post by RichieB07 on 2011-01-19
I did the left+right click and that worked.  Guess it's just something in my hardware that just doesn't want to work.  Oh well.

---

