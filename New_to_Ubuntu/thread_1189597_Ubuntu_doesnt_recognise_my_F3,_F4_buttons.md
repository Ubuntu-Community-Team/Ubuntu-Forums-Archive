---
title: "Ubuntu doesnt recognise my F3, F4 buttons?"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by Psyphre on 2009-06-16
Hi,

I realised today I have alot of F keys and I wanted to assign shortcuts to using gnome shortcuts or compiz commands.

I have a mac keyboard which has F1 all the way to F19.
Alot of these are already binded to media commands, cd ejection, volume etc, however for some odd reason these keys wont:

F3, F4  <---- wont be recognised! Why?

F13 to F19

I dont understand why F3 and F4 arent recognisable. Im pretty sure in previous versions of ubuntu they were. Ideally I wanted to assign F3 to a window switcher, F16 to F19 to each side of the compiz cube.

Any other mac keyboard users having this issue? Or anyone else for that matter.

Thanks in advance.

---

### Post by Psyphre on 2009-06-18
bumpity bump bump ?

---

### Post by tgalati4 on 2009-06-19
xev

---

### Post by Psyphre on 2009-06-19
> **tgalati4 said:**
> xev

sorry?

---

### Post by tgalati4 on 2009-06-19
I presume that you are running "Apple Keyboard" (there are 6 to choose from) in Control Center.

If that doesn't work then:

Run xev in a terminal then press the F3 and F4 keys and compare the output of those keys to working function keys.

You might need to add some instructions at the bottom of /etc/init.d/bootmisc.sh

Here are my keycodes for an HP multimedia keyboard:  (There are 23 extra keys around the top and left side.)

```

# Added new keycodes for sk2506 HP multimedia 23-key keyboard
setkeycodes e016 235
setkeycodes e01e 158
setkeycodes e012 146
setkeycodes e014 148
setkeycodes e015 149
setkeycodes e02d 173
setkeycodes e018 236
setkeycodes e026 238
setkeycodes e017 227
setkeycodes e01f 159
setkeycodes e025 239
setkeycodes e023 237

```

You only need to set key codes if the keys are truly undefined.  If they say something like:

KeyRelease event, serial 34, synthetic NO, window 0x3a00001,
    root 0xae, subw 0x0, time 6305000, (124,100), root:(129,936),
    state 0x0, keycode 246 (keysym 0x1008ff95, XF86WLAN), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

Then you know that this key is mapped to the X-Windows XF86WLAN key.  It happens to be marked "Help" on the keyboard.  You can then assign it to a shortcut or add it to .xmodmaprc in your home directory.

My .xmodmaprc looks like: (for a Gutsy machine)

```

keycode   8 =
keycode   9 = Escape
keycode  10 = 1 exclam
keycode  11 = 2 at
keycode  12 = 3 numbersign
keycode  13 = 4 dollar
keycode  14 = 5 percent
keycode  15 = 6 asciicircum
keycode  16 = 7 ampersand
keycode  17 = 8 asterisk
keycode  18 = 9 parenleft
keycode  19 = 0 parenright
keycode  20 = minus underscore
keycode  21 = equal plus
keycode  22 = BackSpace Terminate_Server
keycode  23 = Tab ISO_Left_Tab
keycode  24 = q Q
keycode  25 = w W
keycode  26 = e E
keycode  27 = r R
keycode  28 = t T
keycode  29 = y Y
keycode  30 = u U
keycode  31 = i I
keycode  32 = o O
keycode  33 = p P
keycode  34 = bracketleft braceleft
keycode  35 = bracketright braceright
keycode  36 = Return
keycode  37 = Control_L
keycode  38 = a A
keycode  39 = s S
keycode  40 = d D
keycode  41 = f F
keycode  42 = g G
keycode  43 = h H
keycode  44 = j J
keycode  45 = k K
keycode  46 = l L
keycode  47 = semicolon colon
keycode  48 = apostrophe quotedbl
keycode  49 = grave asciitilde
keycode  50 = Shift_L
keycode  51 = backslash bar
keycode  52 = z Z
keycode  53 = x X
keycode  54 = c C
keycode  55 = v V
keycode  56 = b B
keycode  57 = n N
keycode  58 = m M
keycode  59 = comma less
keycode  60 = period greater
keycode  61 = slash question
keycode  62 = Shift_R
keycode  63 = KP_Multiply XF86_ClearGrab
keycode  64 = Alt_L Meta_L
keycode  65 = space
keycode  66 = Caps_Lock
keycode  67 = F1 XF86_Switch_VT_1
keycode  68 = F2 XF86_Switch_VT_2
keycode  69 = F3 XF86_Switch_VT_3
keycode  70 = F4 XF86_Switch_VT_4
keycode  71 = F5 XF86_Switch_VT_5
keycode  72 = F6 XF86_Switch_VT_6
keycode  73 = F7 XF86_Switch_VT_7
keycode  74 = F8 XF86_Switch_VT_8
keycode  75 = F9 XF86_Switch_VT_9
keycode  76 = F10 XF86_Switch_VT_10
keycode  77 = Num_Lock Pointer_EnableKeys
keycode  78 = Scroll_Lock
keycode  79 = KP_Home KP_7
keycode  80 = KP_Up KP_8
keycode  81 = KP_Prior KP_9
keycode  82 = KP_Subtract XF86_Prev_VMode
keycode  83 = KP_Left KP_4
keycode  84 = KP_Begin KP_5
keycode  85 = KP_Right KP_6
keycode  86 = KP_Add XF86_Next_VMode
keycode  87 = KP_End KP_1
keycode  88 = KP_Down KP_2
keycode  89 = KP_Next KP_3
keycode  90 = KP_Insert KP_0
keycode  91 = KP_Delete KP_Decimal
keycode  92 =
keycode  93 = Mode_switch
keycode  94 = less greater bar brokenbar bar brokenbar
keycode  95 = F11 XF86_Switch_VT_11
keycode  96 = F12 XF86_Switch_VT_12
keycode  97 = Home
keycode  98 = Up
keycode  99 = Prior
keycode 100 = Left
keycode 101 =
keycode 102 = Right
keycode 103 = End
keycode 104 = Down
keycode 105 = Next
keycode 106 = Insert
keycode 107 = Delete
keycode 108 = KP_Enter
keycode 109 = Control_R
keycode 110 = Pause Break
keycode 111 = Print Sys_Req
keycode 112 = KP_Divide XF86_Ungrab
keycode 113 = Alt_R Meta_R
keycode 114 =
keycode 115 = Super_L
keycode 116 = Super_R
keycode 117 = Menu
keycode 118 =
keycode 119 =
keycode 120 =
keycode 121 =
keycode 122 =
keycode 123 =
keycode 124 = ISO_Level3_Shift
keycode 125 = NoSymbol Alt_L
keycode 126 = KP_Equal
keycode 127 = NoSymbol Super_L
keycode 128 = NoSymbol Hyper_L
keycode 129 =
keycode 130 =
keycode 131 =
keycode 132 =
keycode 133 =
keycode 134 =
keycode 135 =
keycode 136 =
keycode 137 =
keycode 138 =
keycode 139 =
keycode 140 =
keycode 141 =
keycode 142 =
keycode 143 =
keycode 144 = XF86MyComputer
keycode 145 =
keycode 146 =
keycode 147 =
keycode 148 =
keycode 149 =
keycode 150 = XF86Calculator
keycode 151 = XF86Favorites
keycode 152 = 
keycode 153 = XF86Search
keycode 154 = 
keycode 155 =
keycode 156 = NoSymbol Meta_L
keycode 157 =
keycode 158 = XF86Mail
keycode 159 = XF86Documents
keycode 160 = XF86AudioMute
keycode 161 = XF86AudioNext
keycode 162 = XF86AudioPlay XF86AudioPause
keycode 163 = 
keycode 164 = XF86AudioStop
keycode 165 = 
keycode 166 =
keycode 167 =
keycode 168 =
keycode 169 =
keycode 170 =
keycode 171 =
keycode 172 =
keycode 173 =
keycode 174 = XF86AudioLowerVolume
keycode 175 =
keycode 176 = XF86AudioRaiseVolume
keycode 177 =
keycode 178 = XF86Finance
keycode 179 =
keycode 180 =
keycode 181 =
keycode 182 =
keycode 183 =
keycode 184 =
keycode 185 =
keycode 186 =
keycode 187 =
keycode 188 =
keycode 189 =
keycode 190 =
keycode 191 =
keycode 192 =
keycode 193 =
keycode 194 =
keycode 195 =
keycode 196 =
keycode 197 =
keycode 198 =
keycode 199 =
keycode 200 =  XF86Video
keycode 201 =
keycode 202 =
keycode 203 =
keycode 204 =
keycode 205 =
keycode 206 =
keycode 207 =
keycode 208 =
keycode 209 =
keycode 210 =
keycode 211 =
keycode 212 =
keycode 213 =
keycode 214 =  XF86Launch2
keycode 215 =
keycode 216 =
keycode 217 =
keycode 218 =
keycode 219 =
keycode 220 =
keycode 221 =
keycode 222 =
keycode 223 =
keycode 224 =
keycode 225 =
keycode 226 =
keycode 227 =
keycode 228 =
keycode 229 =
keycode 230 =
keycode 231 =  XF86Mail
keycode 232 =  XF86Launch3
keycode 233 =  XF86Launch4
keycode 234 =  XF86Shop
keycode 235 =
keycode 236 =
keycode 237 =
keycode 238 =
keycode 239 =
keycode 240 =  XF86WWW
keycode 241 =  XF86Eject XF86Eject
keycode 242 =  XF86AudioPrev
keycode 243 =  XF86Launch1
keycode 244 =  XF86Phone
keycode 245 =
keycode 246 =
keycode 247 =
keycode 248 =
keycode 249 =
keycode 250 =
keycode 251 =
keycode 252 =
keycode 253 =
keycode 254 =
keycode 255 =

```

You can define keys anyway you want to in Linux.

Apple hardware is proprietary and a moving target, so you have to work harder to get things to work the way they should.

---

### Post by Psyphre on 2009-06-19
thanks, i'll give it a try. Will reply with my progress.

EDIT:

Tried it. As a test I tried the F16 button. It says its key 194

```
KeyPress event, serial 35, synthetic NO, window 0x4800001,
    root 0x13c, subw 0x0, time 11502964, (-734,-6), root:(767,813),
    state 0x0, keycode 194 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x4800001,
    root 0x13c, subw 0x0, time 11503044, (-734,-6), root:(767,813),
    state 0x0, keycode 194 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

So i went to my home directory, created a file called .xmodmaprc
and added this to it:
```
keycode 194 =  F16
```

I assigned a random command like 'terminal' to F16, but no luck, nothing happens when I press it.

---

### Post by tgalati4 on 2009-06-19
What keyboard layout did you set up in Control Center?

You need to reboot, or restart X with Control-Alt-Backspace (which may be disabled in Jaunty).  You don't say which version of Ubuntu that you are using.

Instead of F16 try assigning something already in X-windows such as XF86Calculator or 
F12 XF86_Switch_VT_12.

F16 is not exactly a standard layout.

Also put the keyboard layout switcher in your taskbar.  I have found a bug where the .xmodmaprc don't always get loaded and by clicking on the US Flag (for US keyboard) it reloads it on the spot.  I haven't spent the time to track it down, but that was the behavior in Linux Mint Darnya XFCE based on gutsy.

---

### Post by Psyphre on 2009-06-22
> **tgalati4 said:**
> What keyboard layout did you set up in Control Center?

You need to reboot, or restart X with Control-Alt-Backspace (which may be disabled in Jaunty).  You don't say which version of Ubuntu that you are using.

Instead of F16 try assigning something already in X-windows such as XF86Calculator or 
F12 XF86_Switch_VT_12.

F16 is not exactly a standard layout.

Also put the keyboard layout switcher in your taskbar.  I have found a bug where the .xmodmaprc don't always get loaded and by clicking on the US Flag (for US keyboard) it reloads it on the spot.  I haven't spent the time to track it down, but that was the behavior in Linux Mint Darnya XFCE based on gutsy.

Using Jaunty and using the mac keyboard layout.
I restarted and when i logged back in it asked if i wanted to import the new .xmodmaprc. My F16 is now recognized when I assign it as a shortcut button, yet despite this, it still doesnt do anything. For example I set terminal as the command when I press this button, nothing happens. Or if i set it as a screenshot button.

---

### Post by tgalati4 on 2009-06-22
Try the latest version of Gnome using Foresight Linux. Could be lack of the necessary hook in Gnome. What did you find using a google search for this problem?

---

### Post by Psyphre on 2009-06-22
ACtually I'm starting to think the problem may not necessarily be the keys themselves. I tried assigning ctrl+shift+t to open a terminal. That didnt work. :confused:

I tried 'switch to workspace 1' as the f16 key and that actually worked! but i dont understand why some work and some dont.

> **tgalati4 said:**
> Try the latest version of Gnome using Foresight Linux. Could be lack of the necessary hook in Gnome. What did you find using a google search for this problem?

I didnt find much in google (alot seemed too technical for me). It was basically what you mentioned, but i didnt understand it until you explained how to do it (thanks).

---

### Post by Psyphre on 2009-06-22
update:

Ive had alot of success mapping alot of the keys (thanks to you tgalati4).
F13-F19 are now working for alot of functions I wanted.
Yet strangely F3 and F4 still dont work. Ive even mapped them using the same method. Yet it just wont work.

---

### Post by tgalati4 on 2009-06-22
Is F3 or F4 tied to audio volume or screen brightness?

---

### Post by Psyphre on 2009-06-22
> **tgalati4 said:**
> Is F3 or F4 tied to audio volume or screen brightness?

Nope. ACtually most of my F keys are tied to brightness, audio control, volume, cd eject etc and they all work fine. Yet F3 and F4 arent tied to anything and dont. Its so bizzare!

---

### Post by tgalati4 on 2009-06-22
In a terminal:

dmesg | tail

Note the time (in seconds of the last line)

In another terminal:

Press F3 and F4 a few times and repeat the above command and note the differences.

Also:

cd
cat .xsession-errors

Look for lines like:


** WARNING **: Couldn't grab XF86AudioStop: another client may already have done so

** WARNING **: Couldn't grab XF86AudioRaiseVolume: another client may already have done so

** WARNING **: Couldn't grab XF86AudioLowerVolume: another client may already have done so

** WARNING **: Couldn't grab XF86AudioMute: another client may already have done so

---

### Post by Psyphre on 2009-06-22
> **tgalati4 said:**
> In a terminal:

dmesg | tail

Note the time (in seconds of the last line)

In another terminal:

Press F3 and F4 a few times and repeat the above command and note the differences.

Also:

cd
cat .xsession-errors

Look for lines like:


** WARNING **: Couldn't grab XF86AudioStop: another client may already have done so

** WARNING **: Couldn't grab XF86AudioRaiseVolume: another client may already have done so

** WARNING **: Couldn't grab XF86AudioLowerVolume: another client may already have done so

** WARNING **: Couldn't grab XF86AudioMute: another client may already have done so

Hi, thanks for going to this trouble, I appreciate it.

I have tried what you suggested but I always get the same output:

```
[19263.673393] wlan1: associated
[19263.682102] wlan1: disassociating by local choice (reason=3)
[19296.420834] wlan1: authenticate with AP 00:1c:df:e3:78:ff
[19296.422339] wlan1: authenticated
[19296.422342] wlan1: associate with AP 00:1c:df:e3:78:ff
[19296.424845] wlan1: RX ReassocResp from 00:1c:df:e3:78:ff (capab=0x401 status=0 aid=1)
[19296.424847] wlan1: associated
[27990.248766] npviewer.bin[20037]: segfault at 13 ip 00000000f6ea81b7 sp 00000000ff848584 error 4 in libflashplayer.so[f67f0000+96d000]
[28401.795189] npviewer.bin[20052]: segfault at ff9bea2c ip 00000000ff9bea2c sp 00000000ff8fe49c error 14
[28778.110587] npviewer.bin[20125]: segfault at ff9bea2c ip 00000000ff9bea2c sp 00000000fff1815c error 14
```

even when pressing f3 and f4. No changes. Infact I tried other F keys and no changes between the 2 either.

I also tried your 
cd
cat .xsession-errors

and it gave a huuuuuuuuuge list and said there were too many to display.

---

### Post by tgalati4 on 2009-06-22
less .xession-errors

That will allow you to page through the errors.  Start at the top and take note of the major ones.  Control-C to exit.  Use the spacebar to go forward, backspace to go back or use the arrow keys.

---

### Post by Psyphre on 2009-07-03
well ive got everything working thanks. Except f3 and f4. I guess I'm just gonna have to live with it. Thanks though for the help, i got alot of the other keys mapped and working.

---

