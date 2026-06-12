---
title: "LAN-based Voice Chat?"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by TheBuzzSaw on 2009-03-21
Does anyone know of a good LAN voice chat and/or voice chat server? A friend and I are connected to the same router and play games from our respective apartments. I am looking for a good voice chat solution that does not require the Internet at all. Skype is fabulous but pointless for our particular setup.

---

### Post by HermanAB on 2009-03-21
Skype would be ideal.  It uses SIP and is therefore point to point once the connection is established, so the voice traffic will in effect only run on your LAN.

Cheers,

Herman

---

### Post by TheBuzzSaw on 2009-03-22
Oh, Skype can do that? I need to give that a try.

Where exactly do I go in Skype? I don't see how to established the connection. :(

---

### Post by freak42 on 2009-03-22
I agree: Skype will most likely find out that you're on the same network and not utilize the internet afterwards.

Another (team-chat)-software is teamspeak, it comes with a server and clients which you can setup yourself, this way you know for sure it won't go over the net.

hth

---

### Post by TheBuzzSaw on 2009-03-22
Can Skype do it if I theoretically had no Internet? I'm looking for a tool to use that will work even if the Internet goes down (which it does now and again here).

---

### Post by freak42 on 2009-03-22
> **TheBuzzSaw said:**
> Can Skype do it if I theoretically had no Internet? I'm looking for a tool to use that will work even if the Internet goes down (which it does now and again here).

I don't think so, skype needs their servers to connect to the service and build up a connection afaik, even if afterwards the connection usually is direct between the participants

---

### Post by TheBuzzSaw on 2009-03-24
I just found out about the h323 protocol. Google h323 if anyone is looking for a solution.

Ekiga does in fact support h323. Windows XP has a built-in program called NetMeeting (Start > Run > "conf"). With h323, you can simply make calls to other computers using their IP addresses (those computers need to have Ekiga/NetMeeting/something running in order to receive the call, obviously).

Now I chat with my buddy while gaming, and our respective wives are happy because we can both stay at home. :P

---

