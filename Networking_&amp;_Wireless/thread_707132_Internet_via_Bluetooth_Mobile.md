---
title: "Internet via Bluetooth Mobile"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by viking777 on 2008-02-25
I recently purchased a Sony Ericsson K610i bluetooth enabled mobile and I would like to use it as a modem for my laptop (for which I have a bluetooth dongle). I have been tyring for a week now to make this happen but have got nowhere, so can anyone here help?

Here are some facts. I know the phone modem works because I can connect to the internet on the phone without difficulty. I also know that the bluetooth connection works because I can transfer files to and from the phone via bluetooth and even have the ability (should I ever feel the desire to use it) of enabling the phone as a remote control for certain laptop apps. I am using the '3' network in the UK and I have purchased and activated a 1Gb top up for mobile broadband so I should be set to go.

I have tried kppp, wvdial, and drakconnect (part of Mandriva) in an attempt to get this to work and have spent hours on Google looking for answers but none of the ones I found are relevant to my circumstances. I have also spent hours combing the phone menus to find some way to activate the connectivity but again I have failed. The guide that came with the phone deals only with using the supplied windows software to achieve a connection and thus is useless for me, as is the 3 website and the Sony Ericsson one.

I am using /dev/rfcomm0 as the modem device, which does exist, but any attempt to conect to it results in the message 'modem not responding', and that is about all I can tell you. 

If anyone knows how I can proceed I would be delighted to hear.

---

### Post by viking777 on 2008-02-28
No answers to this thread, so I thought I would give you an update and see if that generates any response. 

I am posting this using my mobile phone modem through a bluetooth conection, but only because I am using Mandriva to do it, I am absolutely unable to do anything with Ubuntu or Linux Mint, and I would like to know why this is, especially in the light of the fact that Mandriva now connects to it easily with either its own utility (drakconnect), kppp or wvdial. 

Initially I wasn't able to connect with Mandriva either, but this was a problem with phone settings which I resolved for myself. As soon as the phone settings were changed Mandriva connected straight away but Ubuntu still won't. The problem seems to be that whilst Mandriva detects and configures a device node for my mobile phone (/dev/rfcomm0 or /dev/rfcomm1) Ubuntu does not do so. I am aware of how to create and bind a device node using the rfcomm command, but whenever I try this and then use wvdial to connect to the created node all I get is 'connection refused'.

Can anyone shed any light on this slightly different problem?

---

