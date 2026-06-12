---
title: "How to play audio file over modem?"
date: 2020-08-28
forum: Networking &amp; Wireless
---

### Post by mfleming on 2020-08-28
Hi,

I'd like to arrange for my server to send a voice message via a serial port and voice modem.  I need a script or program that can dial a number, wait for the answer, then play the audio from a wav or other audio file. My sense is that this might be done with a minicom script, but I don't know how to do it. I could probably figure it out eventually, but if there is already a solution somewhere I'd prefer to use it.

Thanks very much,

Matthew Fleming, MD
Fleming Dermatopathology

---

### Post by TheFu on 2020-08-28
What about using a PBX and having it play any file you like? That's sorta what PBX systems do. There are some pre-setup PBX that run on raspberry pi computers. [http://www.raspberry-asterisk.org/downloads/](http://www.raspberry-asterisk.org/downloads/)

Or you can put the PBX into a container or virtual machine provided the system context switching doesn't introduce too much latency for the audio.

I'm loath to say too much more, since these things can be used for harassment - spam calling thousands and thousands of numbers daily.
[https://wiki.asterisk.org/wiki/display/AST/Asterisk+11+Application_Dial](https://wiki.asterisk.org/wiki/display/AST/Asterisk+11+Application_Dial)  I haven't run a PBX myself in about a decade. Paying $5/month (pre-paid) is much easier for my voice-phone needs after running a FreeSwitch PBX for about 5 yrs. I've never needed automatic outbound calling, just a menu system for inbound calls to make automatic systems stuck for a while, but humans get through easily.

---

### Post by mfleming on 2020-08-29
> **TheFu said:**
> What about using a PBX and having it play any file you like? That's sorta what PBX systems do. There are some pre-setup PBX that run on raspberry pi computers. [http://www.raspberry-asterisk.org/downloads/](http://www.raspberry-asterisk.org/downloads/)

Or you can put the PBX into a container or virtual machine provided the system context switching doesn't introduce too much latency for the audio.

I'm loath to say too much more, since these things can be used for harassment - spam calling thousands and thousands of numbers daily.
[https://wiki.asterisk.org/wiki/display/AST/Asterisk+11+Application_Dial](https://wiki.asterisk.org/wiki/display/AST/Asterisk+11+Application_Dial)  I haven't run a PBX myself in about a decade. Paying $5/month (pre-paid) is much easier for my voice-phone needs after running a FreeSwitch PBX for about 5 yrs. I've never needed automatic outbound calling, just a menu system for inbound calls to make automatic systems stuck for a while, but humans get through easily.

Thanks, but this is overkill for this particular application. In fact I am already running a PBX on a Raspberry Pi for my business. Maybe there is some way to make it do what I want, but if so I don't know how.

I am planning to use the GPIO pins on a Raspberry Pi to monitor a piece of equipment in my lab. It will have a camera trained on the equipment's CRT display (Yes it has a CRT. It's old.) If the equipment errors, the Pi should send a message to the lab's main server, which is connected to a modem. This would then call a technician, who could then look at the display, to see what's wrong. (The Pi can take pictures of the display, say once per minute, and also send those over to the server, where they would be visible via the webserver.)

I know how to make all this happen except for placing the call!

---

### Post by TheFu on 2020-08-29
To control dialing on any model, use 'AT' commands.  It has been decades since I did that. I don't know how to make audio go through the connection by playing back a file. Can't be that hard, but if you haven't been able to figure it out, it must not be intuitively obvious. Hate when that happens.  [https://iotbytes.wordpress.com/play-audio-file-on-phone-line-with-raspberry-pi/](https://iotbytes.wordpress.com/play-audio-file-on-phone-line-with-raspberry-pi/) seems to be exactly what you want.  You must have seen that.  Was there some difficulty?  AT+VTX 

Another option would be sending a text.  Texting a phone number is usually just sending an email to a public number for the person which is pretty trivial for internet connected Unix systems. Of course, maybe in a lab, the computers are air-gapped from the internet. Just throwing out an option.

---

### Post by mfleming on 2020-08-29
> **TheFu said:**
> To control dialing on any model, use 'AT' commands.  It has been decades since I did that. I don't know how to make audio go through the connection by playing back a file. Can't be that hard, but if you haven't been able to figure it out, it must not be intuitively obvious. Hate when that happens.  [https://iotbytes.wordpress.com/play-audio-file-on-phone-line-with-raspberry-pi/](https://iotbytes.wordpress.com/play-audio-file-on-phone-line-with-raspberry-pi/) seems to be exactly what you want.  You must have seen that.  Was there some difficulty?  AT+VTX 

Another option would be sending a text.  Texting a phone number is usually just sending an email to a public number for the person which is pretty trivial for internet connected Unix systems. Of course, maybe in a lab, the computers are air-gapped from the internet. Just throwing out an option.

I found the posting you referenced and tried running the program. It doesn't work with my modem, for some reason, and in any case doesn't do what I want, because it is designed to receive, not send, a voice message.

Yes, there are AT commands.  A lot of them. I'm afraid this is a lot more complicated then sending AT+VTX.

---

