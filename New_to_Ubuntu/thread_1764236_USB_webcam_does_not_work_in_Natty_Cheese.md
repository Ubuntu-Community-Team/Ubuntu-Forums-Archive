---
title: "USB webcam does not work in Natty Cheese"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by rbowen1 on 2011-05-21
[SIZE=3]Recent install of Natty.   Experienced IT support but new to Linux.  [/SIZE]

                       #toc, .toc, .mw-warning { border: 1px solid rgb(170, 170, 170); background-color: rgb(249, 249, 249); padding: 5px; font-size: 95%; }#toc h2, .toc h2 { display: inline; border: medium none; padding: 0pt; font-size: 100%; font-weight: bold; }#toc #toctitle, .toc #toctitle, #toc .toctitle, .toc .toctitle { text-align: center; }#toc ul, .toc ul { list-style-type: none; list-style-image: none; margin-left: 0pt; padding-left: 0pt; text-align: left; }#toc ul ul, .toc ul ul { margin: 0pt 0pt 0pt 2em; }#toc .toctoggle, .toc .toctoggle { font-size: 94%; }body { font-family: 'Times New Roman'; color: rgb(0, 0, 0); widows: 2; font-style: normal; text-indent: 0in; font-variant: normal; font-weight: normal; font-size: 12pt; text-decoration: none; text-align: left; }table {  }td { border-collapse: collapse; text-align: left; vertical-align: top; }p, h1, h2, h3, li { color: rgb(0, 0, 0); font-family: 'Times New Roman'; font-size: 12pt; text-align: left; }         [COLOR=#3c3c3c][FONT=monospace]Known good generic webcam[/FONT][/COLOR]
    
    [COLOR=#3c3c3c][FONT=monospace]gstreamer-properties[/FONT][/COLOR]
    [LEFT][COLOR=#3c3c3c][FONT=monospace]shows that I have V4l2 only.   Try test & get:[/FONT][/COLOR][/LEFT]
    [LEFT]Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'.

[/LEFT]
    [LEFT][/LEFT]
    [COLOR=#3c3c3c]Ran   dmesg  & here is relevant output [/COLOR]
    
    [LEFT]rio0/input/input2[/LEFT]
    [LEFT][    0.767712] usb 1-1: new high speed USB device using ehci_hcd and address 2[/LEFT]
    [LEFT][/LEFT]
    [LEFT][   22.368089] uvcvideo: Found UVC 1.00 device USB2.0 Camera (1e4e:0102)[/LEFT]
    [LEFT][   22.375317] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.[/LEFT]
    [LEFT][   22.389162] input: USB2.0 Camera as /devices/pci0000:00/0000:00:10.4/usb1/1-1/1-1:1.0/input/input3[/LEFT]
    [LEFT][   22.401931] usbcore: registered new interface driver uvcvideo[/LEFT]
    [LEFT][   22.401936] USB Video Class driver (v1.0.0)[/LEFT]
    [LEFT][/LEFT]
    [LEFT][/LEFT]
    [LEFT]76.296056] uvcvideo: Failed to resubmit video URB (-27).[/LEFT]
    [LEFT][   76.296069] uvcvideo: Failed to resubmit video URB (-27).[/LEFT]
    [LEFT][   76.296077] uvcvideo: Failed to resubmit video URB (-27).[/LEFT]
    [LEFT][   76.296085] uvcvideo: Failed to resubmit video URB (-27).[/LEFT]
    [LEFT][   76.296091] uvcvideo: Failed to resubmit video URB (-27).[/LEFT]
    [LEFT][  269.020032] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/LEFT]
    [LEFT][  274.032026] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/LEFT]
    [LEFT][  279.044033] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/LEFT]
    [LEFT][  284.056027] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/LEFT]
    [LEFT][  289.068036] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/LEFT]
    [LEFT][  294.080027] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/LEFT]
    [LEFT][  299.092025] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/LEFT]
    [LEFT][  304.104022] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/LEFT]
    [LEFT][  309.140025] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/LEFT]
    [LEFT][  314.152026] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/LEFT]
    [LEFT][  319.164026] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/LEFT]
    [LEFT][  324.176104] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/LEFT]
    [LEFT][  329.188025] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/LEFT]
    [LEFT][  334.200025] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/LEFT]
    [LEFT][  339.212025] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/LEFT]
    [LEFT][  344.228024] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/LEFT]
    [LEFT][  441.028017] ehci_hcd 0000:00:10.4: force halt; handshake f800e014 0000c000 00000000 -> -11


Could this be a driver issue?


Any help will be appreciated.  
[/LEFT]

---

### Post by no2498 on 2011-05-22
seen this some time ago you may try it

BicyclerBoy 
Skinny Soy Caramel Ubuntu

  
Join Date: Apr 2009
Location: Aotearoha
 Beans: 656 
 Ubuntu 10.04 Lucid Lynx 	Re: Webcam not working (Dell SP2208WFP) 
Try from terminal
rmmod uvcvideo
 modprobe uvcvideo
 dmseg

 Repeat these (<5) until the camera initialises okay..

 You could try this ppa to update some v4l components..

[https://launchpad.net/~libv4l/+archi...ilter=maverick](https://launchpad.net/~libv4l/+archi...ilter=maverick)


sudo rmmod uvcvideo
sudo modprobe uvcvideo

---

