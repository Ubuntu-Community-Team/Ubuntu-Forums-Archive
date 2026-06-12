---
title: "How-To: Use ethernet cable for wireless cards"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by eggie9001 on 2008-08-17
If you have a laptop (or a desktop?) that won't recognize your wireless network card, all you have to do is follow these steps.

1) Things you'll need:
   a) An ethernet cable connected to your wireless router
   b) The computer you are having troubles with

2) Plug the ethernet cable into the wired network input in your computer (LAN?)

3) Install all of the updates with update manager.
   System -> Administration -> Update Manager

4)When this is finished, go into your hardware drivers.
  System -> Administration -> Hardware Drivers

5) Look for Broadcom B43 wireless driver

6) Click enable and you're finished! :)

If there are any holes in this tutorial or if is in the wrong section, sorry for any inconveniences. Please tell me about missing parts.

---

### Post by pytheas22 on 2008-08-17
This is a good tutorial, but what you should mention is that it's only for wireless cards with Broadcom chipsets (you can see which chipset you have using the "lspci" command, or "lsusb" for USB cards), as the b43 driver only supports Broadcom cards.  So I would recommend putting Broadcom in the thread title.

---

