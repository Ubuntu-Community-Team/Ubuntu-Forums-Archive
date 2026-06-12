---
title: "Cisco IP  phone"
date: 2020-09-26
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2020-09-26
I asked in the cisco community forum for help to trace why my phone is not showing in its directory the phone numbers recorded in my web portal at broadcloud. They should have been downloaded and incorporated into the phone's  directory. I have done a number of restarts to no effect on the contents of the directory. 

This is the initial response:

*There's not so much you can do itself. Turn on and catch syslog&debug messages (highest level possible). Catch all network packets send/received by your phone as well. It may help you (or us if you disclose them) to guess the cause.*

Each phone on my network has its own url eg 192.168.1.173

What is the simplest way for me to catch the relevant network packets?

I am using 18.04

---

### Post by dan163 on 2020-09-26
I would recommend using wireshark. you can filter results by ip address, and put the phones ip in

[https://linuxhint.com/install_wireshark_ubuntu/](https://linuxhint.com/install_wireshark_ubuntu/)

---

### Post by Robbyx on 2020-09-27
thank you. It looks daunting, but I will try.

---

### Post by Robbyx on 2020-09-29
I have not been able to understand how to use Wireshark to check why the directory of phone numbers and names  is not being downloaded into the phone. I would very much appreciate some detailed guidance.

---

