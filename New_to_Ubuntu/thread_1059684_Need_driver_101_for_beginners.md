---
title: "Need driver 101 for beginners"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by kakotako on 2009-02-04
I'm reading the Pocket Guide right now. Forgive me if I'm asking this question prematurely should the answer be contained within the book.

Could someone point me to a device drivers primer. I would like to learn how drivers are installed and removed from Ubuntu, what are the things to watch for, etc.

I have a new Dell Mini 9 with 8.04 installed. I want to replace the wireless card driver with one that would allow me to use the adapter in RF monitor mode but I am scared of breaking a perfectly good system.

---

### Post by Crafty Kisses on 2009-02-04
There's a couple of ways of installing drivers, depending on what kind of driver you want to install there's different ways, let me list them:
[LIST]
[*]Hardware Drivers option
[*]Ndiswrapper
[*]Compile drivers from source
[*]Synaptic Package Manager
[/LIST]
So let's begin from the top, the Hardware Drivers can detect anything from graphics card drivers to wireless card drivers. It can be accessed by going to **System->Administration->Hardware Drivers**, simple enough right? 

Ndiswrappers can be a little complicated, but don't worry here is great documentation on it: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper). 

Then there's the option to compile the driver from source, which usually means you can download the Linux driver off of your manufactures website, and then compile them, here's great documentation on HOWTO compile from source: [https://wiki.ubuntu.com/CompilingSoftware](https://wiki.ubuntu.com/CompilingSoftware).

Then there's Synaptic Package Manager, there are sometimes drivers  in here you can look for, just search it up and Synaptic and maybe you will have some luck, who knows right?

---

