---
title: "Wireless question"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by Extract_Here on 2009-12-21
Are most new laptops able to connect with a wireless card when you first install ubuntu?

Or do you still have to use Ndiswrapper to get your connection.

---

### Post by Grenage on 2009-12-21
Most are ok now.  You might need to have a wired connection when you start, just in case the drivers aren't included.  That happened to me, so I just hooked it up via a cable, did and apt-get update and then went to Administration/Hardware Drivers/.

---

### Post by snowpine on 2009-12-21
It depends entirely on the specific hardware... some cards are well-supported, while others aren't (usually due to the manufacturer not providing open source drivers).

You can use the terminal command 'lspci' (without the quotes) to figure out exactly which card you have, then use the forum search feature to find answers. Or, just boot with a Live CD and see for yourself.

Ndiswrapper is no longer recommended (since kernel 2.6.30 I believe).

---

### Post by nishant.singh28 on 2009-12-21
My Dell Studio 1555's wireless works fine...

---

