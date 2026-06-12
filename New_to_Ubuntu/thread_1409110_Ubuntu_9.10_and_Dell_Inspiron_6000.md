---
title: "Ubuntu 9.10 and Dell Inspiron 6000"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by horgzter on 2010-02-17
Hi,

I just installed Ubuntu for the first time on my old laptop. 

Now I am going to use it as a server for my files and play music/video to stero and TV. 

But I cant get any output signal to the TV - I am using S-video as the connection. 

Any possibilities?

---

### Post by tom.swartz07 on 2010-02-17
> **horgzter said:**
> Hi,

I just installed Ubuntu for the first time on my old laptop. 

Now I am going to use it as a server for my files and play music/video to stero and TV. 

But I cant get any output signal to the TV - I am using S-video as the connection. 

Any possibilities?

Hiya! Congrats on making the plunge!

Could you specify what kind of graphics card you have on the laptop? It might be the case that it doesnt support TV-out, despite the fact that it may have worked with Windows.


You could run the command 
```
sudo lshw -C Display
```

To see whats listed; copy and paste the output here. 




Ive mentioned this to quite a few people who have cards on their computers that dont support TV-out- you could get a Scan Converter for a relative cheap price that works really well- in fact, its what I have hooking this computer up to an old LCD tv! 
You could find examples here: [http://www.amazon.com/VideoSecu-VGA2TV-Computor-Presentation-Converter/dp/B000X3FAJU/ref=dp_cp_ob_e_title_0](http://www.amazon.com/VideoSecu-VGA2TV-Computor-Presentation-Converter/dp/B000X3FAJU/ref=dp_cp_ob_e_title_0)

---

### Post by horgzter on 2010-02-17
display UNCLAIMED     
       description: VGA compatible controller
       product: M22 [Mobility Radeon X300]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-d7ffffff(prefetchable) ioport:de00(size=256) memory:dfdf0000-dfdfffff memory:dfd00000-dfd1ffff(prefetchable)


Yeay, it worked fine with windows XP. When I press the familiuar buttons (fn+f8)the screen blinks but nothing happens. It does not detect any tv-monitor in the monitor-settings.

---

### Post by tom.swartz07 on 2010-02-17
> **horgzter said:**
> display UNCLAIMED     
       description: VGA compatible controller
       [COLOR="Red"]**product: M22 [Mobility Radeon X300]**[/COLOR]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-d7ffffff(prefetchable) ioport:de00(size=256) memory:dfdf0000-dfdfffff memory:dfd00000-dfd1ffff(prefetchable)


Yeay, it worked fine with windows XP. When I press the familiuar buttons (fn+f8)the screen blinks but nothing happens. It does not detect any tv-monitor in the monitor-settings.

Yep, just as I thought. You have an old ATI card, an X300. Mine is an X1270 and, just like you, its unsupported.

You have 2 options; you could install ubuntu 8.04 and get the official driver for your display (thats what I did on here, but i only sometimes use it), or you could purchase the Scan Converter.

ATI is terrible with the support for all of their cards, the X1200 series was released back in 2007, and no more than 6 months later they put the card on 'legacy' support; meaning that it wont receive any updates at all. Your card is in the same boat. 

Sorry! I hope that I at least cleared up some confusion though!

---

### Post by horgzter on 2010-02-17
It is not possible to import the driver from 8.04?

Is there any significant differences in 8.04 and 9.10?

I just finished installing the server/remote desktop programs, with some help so hope to keep it.

---

### Post by tom.swartz07 on 2010-02-17
> **horgzter said:**
> It is not possible to import the driver from 8.04?

Is there any significant differences in 8.04 and 9.10?

I just finished installing the server/remote desktop programs, with some help so hope to keep it.

Nope, the driver for 8.04 only works on the old version of XOrg thats packaged with it. 


Basically the only difference between 8.04 and 9.10 is that 9.10 comes with newer versions of many core programs; dont confuse 'newer' with 'better working'- the old versions work great on their own, but the new versions may have more functionality. When developers get lazy COUGHCOUGH-ATI-COUGH the versions of programs that worked in one version might 'break' in the next. Thats all.
99.9% of the time devs have support for the new version months before its widely available to the public. 



If you really dont want to re-install, just shoot for the scan converter then- its $30 and you could toss it in your bag to take with you wherever you go.

---

### Post by horgzter on 2010-02-17
The scan converter (new to me) looks very similar to my cable-tv box?

Could it be I can connect it to this? It has a S-video/jack plug for picture and two sound connections. I would guess these are inputs and not output channels.

---

### Post by tom.swartz07 on 2010-02-17
> **horgzter said:**
> The scan converter (new to me) looks very similar to my cable-tv box?

Could it be I can connect it to this? It has a S-video/jack plug for picture and two sound connections. I would guess these are inputs and not output channels.

Are you sure? its only about 6inches by 3 inches and maybe 2 inches high. Just a little guy.


it just has video out; vga, s-video, yellow rca

---

### Post by horgzter on 2010-02-17
Will check - probably not. 

This thing?

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by tom.swartz07 on 2010-02-17
> **horgzter said:**
> Will check - probably not. 

This thing?

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

nope- dont use that- thats specifically for nVidia cards, you have ATI. If you install/use that, youll end up with a broken system.

---

### Post by horgzter on 2010-02-17
I loaded 8.04 onto a USB-stick - did not find any TV-screen when running live from the USB. 

Can you guide me into using this version and getting it to work? 

Thank you very much for the help so-far!

---

### Post by achase79 on 2010-02-17
Did you try downloading and installing the driver from AMD/ATI's website?
[http://support.amd.com/]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.4&lang=English")

---

### Post by tom.swartz07 on 2010-02-17
> **horgzter said:**
> I loaded 8.04 onto a USB-stick - did not find any TV-screen when running live from the USB. 

Can you guide me into using this version and getting it to work? 

Thank you very much for the help so-far!

When you boot up in 8.04, after about 1 or 2 minutes a restricted drivers bubble will pop up from the notification area. From there you could install the drivers needed. 

Alternatively, you could follow the advice above me- 

Right here is the driver you need to install. [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.21&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.21&lang=English)

I must note that you need to make the USB persistent for the driver to take hold, once you install it, it needs to stay there; a liveUSB will not do that. 


pendrivelinux has good info on making your premade usb persistent. basically all you need is a casper-rw file and to change 1 line of code.

---

### Post by horgzter on 2010-02-17
Hi,

Now writing while looking at my TV-monitor! Great success!!!! 
I installed 8.04 as a side-by-side installation with 9.10. Guess I can remove the 9.10 later on, but that will wait (any tips on how to re-enable that partitionto 8.04 one is appreciated though!)

Now I only need to redo the remote desktop/sftp stuff - hope I will find out how!

Again - thank you so much!

---

