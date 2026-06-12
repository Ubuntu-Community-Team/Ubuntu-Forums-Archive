---
title: "Internet not working"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by SonicReducer on 2008-05-02
I'm sure these posts are common ground now but after browsing through them all I've yet to have had my problem solved.

Ok I bought a 2nd hand laptop and took it as an opportunity to install Ubuntu onto it (using 7.04) As far as I can tell it all installed fine but when it comes to using it, everything works but the internet in any form.

I'm mostly connected to the web via a wired network but the laptop also has a wireless card, which won't even detect.

The laptop as I said is second hand and thus is outdated (I'm a poor student ok?) its a Toshiba TE2300 (thats all I know in regards to model), and the most of the hardware is intel including the ethernet.

I'm a noob for the most part so don't expect me to understand everything you sling at me, thanks.

---

### Post by superprash2003 on 2008-05-02
are you getting an ip address? could you post ifconfig output?

---

### Post by SonicReducer on 2008-05-02
Since I'm on 2 different computers right now its a tad difficult so I will just retype it.

lo        Link encap:Local Loop back
          intet addr:127.0.0.1  Mask: 255.0.0.0
          Inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTY:16436 Metric:1
          RX packers: 48 erros:0 dropped:0 overruns:0 frame:0
          TX packers:48 errors:0 dropped:0 overruns:0 carrier:0
          collions:0 txqueuelen:0
          RX byes: 3584 (3.5 kb)  TX byes: 4584 (3.5kb)

---

### Post by Trog on 2008-05-02
What's the output of sudo lshw -C network 

Do you see 2 network interfaces listed?

Can the wireless be disabled/enabled in BIOS?

The Toshiba kit we use at work has a tiny slide switch on the side to turn the wireless on/off. Just a thought.

---

### Post by tech9 on 2008-05-02
> **SonicReducer said:**
> Since I'm on 2 different computers right now its a tad difficult so I will just retype it.

lo        Link encap:Local Loop back
          intet addr:127.0.0.1  Mask: 255.0.0.0
          Inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTY:16436 Metric:1
          RX packers: 48 erros:0 dropped:0 overruns:0 frame:0
          TX packers:48 errors:0 dropped:0 overruns:0 carrier:0
          collions:0 txqueuelen:0
          RX byes: 3584 (3.5 kb)  TX byes: 4584 (3.5kb)

It doesn't look like you are being assigned an IP address - There's your problem

---

### Post by superprash2003 on 2008-05-02
your ifconfig shows only lo??you dont have any eth0 or wlan0? then its either a drivers issue or you have disabled it... could you recheck your ifconfig

---

### Post by SonicReducer on 2008-05-02
Hi, Rechecking the Ifconfig gives the same result, as far as I know the correct drivers are installed (if not I'd appreciate any direction in finding them). Also if its disabled how to I enable it then?

also as for doing the "sudo lshw -C network" command it does appear to have two networks, but ironically as mentioned above they do appear as "disabled" or "unclaimed" how do i fix this?

---

### Post by SonicReducer on 2008-05-03
anyone have any ideas?

---

### Post by SonicReducer on 2008-05-03
anyone know anywhere i can find drivers that will work with ubuntu

---

### Post by Trog on 2008-05-03
I'm so fed up with the hardware issues (crackly sound and no network) that I'm going to downgrade back to Gutsy Gibbon, it may not have LTS but at least it works.

---

### Post by SonicReducer on 2008-05-04
If only it was that easy for me. Anyone know how to fix this issue please help!

---

### Post by SonicReducer on 2008-05-04
Just adding that my network card is a intel pro/100 if that will help anyone help me.

---

### Post by Trog on 2008-05-05
Can you clarify for me. Are the wired ethernet and Wireless ethernet built in or on a PCMCIA plug-in card.?

---

