---
title: "Ubuntu blocking internet"
date: 2023-11-20
forum: Networking &amp; Wireless
---

### Post by yeshua-1 on 2023-11-20
Ubuntu  22.04.3 Stopped allowing internet connection. Connects to wireless and settings shows the link speed but all programs return no internet detected error. Check wireless on other devices, internet is in the wireless. Tried wired connection to computer, same result, settings shows connection speed but no program can obtain an internet connection. Checked firewall, turning it off made no difference. Checked if hardblock through rfkill list command. No hard block. Stumped. Downloaded wireless info.txt, transferred and ran. Results a single ###wireless info start###, but nothing more. Suggestions?

---

### Post by TheFu on 2023-11-21
Can you ping the router and other systems on your LAN?
Can you ping the public IP on your router?
Can you ping well-known public IPs, like 1.1.1.1 and 8.8.8.8?
Can you 'dig' google.com?

Is it 1 system or every system on your LAN with the issue?

After running those tests, you should be able to tell if it is truly a network issue as compared to just a DNS problem.  To non-technical people, DNS failures can easily seem like network problems.

May I recommend that you solve the wired ethernet issue first?  wifi problems quickly go down a rabbit hole of issues that are best avoided with a CAT5e cable.

---

### Post by yeshua-1 on 2023-11-22
I cannot ping those numbers.
Just 1 system.
I did try using a CAT5e cable, same problem.
Problem persists.

---

