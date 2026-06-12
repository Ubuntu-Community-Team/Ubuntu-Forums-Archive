---
title: "Wireless problems"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by David Keenliside on 2008-04-13
I have just installed ubunto7.04  on  previous windows laptop and removed the windows. i have aol speedwell router which works ok with my windows desktop and will also work on the ubunto laptop when connected to the router via an ethernet cable. I cannot access the internet using the ubunto laptop when on wireless though the wireless is on and can see my network and also neighbours and I have set it up correctly. I get the message unable to connect to server. Is this an aol thing? and is there any way around this. I would be greatful for any advice
regards
David

---

### Post by kutjara on 2008-04-13
> **David Keenliside said:**
> I have just installed ubunto7.04  on  previous windows laptop and removed the windows. i have aol speedwell router which works ok with my windows desktop and will also work on the ubunto laptop when connected to the router via an ethernet cable. I cannot access the internet using the ubunto laptop when on wireless though the wireless is on and can see my network and also neighbours and I have set it up correctly. I get the message unable to connect to server. Is this an aol thing? and is there any way around this. I would be greatful for any advice
regards
David

Are you using the same security settings (WEP/WPA/WPA2) on the laptop and the router? Have you entered the correct password? Is the router expecting a hexadecimal password and you've entered ASCII (or vice-versa)? If using hex, does your router require any special characters (like '$' or 'xO') to let it know the characters are hex?

These are just a few of the things that can stop a connection from being established. One problem I've seen with Windows, for example, is that it will allow a 25 character ASCII password under 128 bit WEP (when it should only allow 13 characters). If you try to use the same password on Macs or Linux boxes, they won't allow you to type more than 13 characters, so you can't connect without changing the password on the router to one that's 13 characters long. Some of the biggest problems people have with connecting wirelessly to systems that have been set up under Windows, is that Windows' wireless setup process is sloppy and noncompliant.

---

### Post by David Keenliside on 2008-04-13
I have tried hex and ascii, also am using wep and correct password. My wife's vista machine works fine but I used an aol settup diisc on that and cannot on the ubunto machine. I am just intrigued that I can use the internet on the ubunto computer when I connect to the router by ethernet cable but the wireless will not work with it

---

### Post by kutjara on 2008-04-13
> **David Keenliside said:**
> I have tried hex and ascii, also am using wep and correct password. My wife's vista machine works fine but I used an aol settup diisc on that and cannot on the ubunto machine. I am just intrigued that I can use the internet on the ubunto computer when I connect to the router by ethernet cable but the wireless will not work with it

Actually, being able to connect via Ethernet but not via wifi is very common. It's usually the means by which I get my wifi working with a new installation (hook up to the Net via ethernet, download the necessary wifi drivers, compile and install, connect). Ethernet card technology is pretty stable. Consequently, the drivers built-in to Ubuntu tend to work well with most of the cards on the market.

Wifi, on the other hand, is a very unstable market, with new cards hitting the shelves almost daily. The Linux community has a real challenge on its hands keeping up with the rapidly changing landscape. So, whenever I install Linux on a new machine, I expect ethernet will work and wifi won't.

Also, of course, your router just passes signals from the ethernet port straight through to your cable/dsl box. There's no security layer to configure, so problems of passwords and protocols don't arise.

OK, back to your problem. What flavor of WEP are you using? 40 bit, 64 bit, 128 bit? Is your password in Windows the recommended length for the encryption strength you're using (for example, WEP 128 uses 13 characters for ASCII passwords or 26 characters for hex)? If you look at the edits I made to my previous post, you'll see I described how some of the choices Windows makes in its wifi settings can foul things up for people on Macs or Linux boxes.

---

### Post by David Keenliside on 2008-04-13
Thanks for your suggestions I am relieved to know there can be difficulties with the wireless connections, i thought it was all me,  it was just that it worked so easily on the vista laptop and I have not experienced linux before.  I will check the encription I am not sure without checking what type of wep it is and i will go through your other suggestions. thanks again for your help
regards
david

---

### Post by kutjara on 2008-04-13
> **David Keenliside said:**
> Thanks for your suggestions I am relieved to know there can be difficulties with the wireless connections, i thought it was all me,  it was just that it worked so easily on the vista laptop and I have not experienced linux before.  I will check the encription I am not sure without checking what type of wep it is and i will go through your other suggestions. thanks again for your help
regards
david

Wireless is still one of the problem areas for Linux. Mark Shuttleworth has promised that the next version after Hardy will be all about wireless networking, so I'll be interested to see if there's a magic bullet in the works to make setting up wireless cards a less agonizing process.

Good luck, and if you continue to have problems, I'm happy to help if I can.

---

