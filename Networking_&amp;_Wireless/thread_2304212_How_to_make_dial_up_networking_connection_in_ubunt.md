---
title: "How to make dial up networking connection in ubuntu 15.10"
date: 2015-11-24
forum: Networking &amp; Wireless
---

### Post by Manoj_Arun_Kumar on 2015-11-24
Hi, 

I am using Nokia C2-00.
I wanted to establish dialup connection between my mobile & my ubuntu system 15.10 via bluetooth.
I have tried in windows 7 and its working fine.

When i try to connect with DUN using blueman in ubuntu 

I am getting either of the following error messages :

connection failed : Message recipient disconnected from message bus without replying

or

Connection Failed: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/blueman/services/meta/SerialService.py", line 29, in connect
    port_id = create_rfcomm_device(Adapter(props['Adapter']).get_properties()['Address'], props['Address'], 1)
  File "_blueman.pyx", line 214, in _blueman.create_rfcomm_device (_blueman.c:2006)
Exception: Can't connect RFCOMM socket


Can anyone pls guide me to solve this issue .

Regards
MAK

---

