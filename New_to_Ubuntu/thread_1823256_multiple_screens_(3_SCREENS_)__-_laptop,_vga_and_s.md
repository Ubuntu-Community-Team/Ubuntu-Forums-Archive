---
title: "multiple screens (3 SCREENS )  - laptop, vga and s-video"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by Cyjan on 2011-08-11
**VGA+SVideo+Laptop_screen ---all at once?  --- 3 screens from laptop's motherboard is it possible????**             
                                                                Is it possible to have 3 screens desktop straight from my laptop?
laptop can recognize all 3 screens connected it can detect their size and resolution! ( see the screenshot )
but when i try to turn all 3 on on of them will always go off.

---

### Post by papibe on 2011-08-11
AFAIK, most graphic cards only support two outputs at the same time.

But anyway, what is your GPU, or integrated graphics?

Regards.

---

### Post by JC Cheloven on 2011-08-11
In [this screencast]("http://lubuntu.net/blog/lubuntu-screencast-multi-monitor-tips-tricks") he tells about second or third monitor... 
There are useful tips based on lxrandr, xrandr amd arandr that should apply almost equally for the gnome (or unity) versions of ubuntu.

Hope this helps

---

### Post by Cyjan on 2011-08-11
graphics card is integrated. 

system gives me error : ctrc ( see  screenshot )

thanks!

---

### Post by Cyjan on 2011-08-11
> **JC Cheloven said:**
> In [this screencast]("http://lubuntu.net/blog/lubuntu-screencast-multi-monitor-tips-tricks") he tells about second or third monitor... 
There are useful tips based on lxrandr, xrandr amd arandr that should apply almost equally for the gnome (or unity) versions of ubuntu.

Hope this helps


thanks for that, although i had arandr installed and it behavies just like ubuntu's "monitor preferences"
i tried in terminal command xrandr --auto but i've got 

"xrandr: cannot find crtc for output VGA1"

as a result.
 
how can i make crtc?

---

### Post by JC Cheloven on 2011-08-12
mmm... this is probably due to a proprietary video driver being installed in your system. Is there any? (you can check this simply by opening the "additional controlers" item that should be in your system admin menu). If so, there should be some application installed in your system to fiddle with monitors (also usable for color correction, etc).

[INDENT]Some background: I've an nvidia graphics card. When I used the *libre* driver I was able to control the brightness of the screen (I like it well below the standard minimal brightness), and every related thing using xrandr. But when I use the nvidia proprietary driver, I have to use the application provided by nvidia (works fine anyway).[/INDENT]

Also, please post the output of the command xrandr (without any arguments), and that of the comand lspci. Thank you.

---

### Post by Cyjan on 2011-08-13
[FONT=Courier New][SIZE=1][SIZE=2][FONT=Arial]i can't find the "additional controllers". 

here is what lspci gives me :
[/FONT][/SIZE]

 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)[/SIZE][/FONT]

[SIZE=3]
and xrandr gives me: [SIZE=2](sorry not sure which arguments you don't need)[/SIZE][/SIZE]

[FONT=Courier New][SIZE=1]Screen 0: minimum 320 x 200, current 2128 x 800, maximum 8192 x 8192
VGA1 connected (normal left inverted right x axis y axis)
   1280x1024      60.0 +   75.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
DVI1 disconnected (normal left inverted right x axis y axis)
TV1 connected 848x480+1280+0 (normal left inverted right x axis y axis) 0mm x 0mm
   848x480        30.0*+
   640x480        30.0 +
   1024x768       30.0  
   800x600        30.0 [/SIZE][/FONT]



thanks!

---

### Post by papibe on 2011-08-13
I did some 'googling', and [this ]("http://askubuntu.com/questions/25954/is-it-possible-to-use-more-than-two-monitors")pop out. Sadly, it seems that there's no much hope for this to work.

Regards.

---

### Post by JC Cheloven on 2011-08-15
Sorry for the delay, I was out yesterday.

I also see [here]("http://superuser.com/questions/229010/3-monitor-pci-e-graphics-card-on-linux-without-tremendous-pain/") that more than 2 monitors need either a professional grade video card, 
[INDENT]OR[/INDENT]
one of the displays being connected through an active adapter. This seems to be a piece of hardware I don't know about (never had the need). The guy tolds us in the update that things seemes to work with this. Here an excerpt: 
> I got my active adapter in the mail today (it's DisplayPort to DVI) and so far things seem to be better. I can run my third screen, drag things seamlessly between them, and I am also running compiz. The adapter I'm using is a "B087B-005B" made by "Accell", UPC is "826388106239".
So I guess there's little point in messing around with the xrandr command ATM (papibe was right at this in the first place =D> ). Things should work right away with the needed thingie. Sorry to be unable to point you further on this point. 

Best
JC

---

### Post by Cyjan on 2011-08-15
thank you very much tor all your help

i certainly have much better control over my 3 screens now, with xrandr and arandr and its amazing ".sh"  files that i really really like

thank you

---

