---
title: "VPN broken with 24.04 - works with 20.04"
date: 2024-11-07
forum: Networking &amp; Wireless
---

### Post by kaktux on 2024-11-07
Hi,

i have a problem getting my (open)vpn connection to work properly after updating from LTS to LTS - (kubuntu) 20.04 to 24.04.

The connection works fine with the old installation -but not the new one. It works EVEN in a virtual machine running 20.04 - but not on the 24.04 installation the virtual machine runs in...

The first error that came up is the connection asking over and over again for a password - which can be solved by replacing[URL="https://www.reddit.com/r/Ubuntu/comments/1esqudv/vpn_issues_on_2404/"] replace ‘cipher AES-128-CBC’
with ‘data-ciphers-fallback AES-128-CBC’  as described here[/URL].
With this the vpn sucessfully connects - and even using samba connection to my qnap-nas works, also logging in to the nas via browser.
But i also have other software installed that can be accessed via browser - but not with the 24.04 installation..
Whenever i try to access this software via browser it just loads and loads - but nothing happens. Starting the 20.04 VM it just works.


Are there any know issues with VPN on 24.04 that i oversaw? I searched for some time now - but all i found were solutions that didnt work for me.
Do you have any idea what might cause this problem? 
Any tip or help is much appreciated.

---

