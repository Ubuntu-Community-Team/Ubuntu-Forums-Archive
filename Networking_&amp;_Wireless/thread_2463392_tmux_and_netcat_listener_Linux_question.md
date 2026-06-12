---
title: "tmux and netcat listener Linux question"
date: 2021-06-10
forum: Networking &amp; Wireless
---

### Post by adriaan4 on 2021-06-10
Hello all,

Recently I picked up a new NB-IoT project, and started playing around with Linux and some NB-IoT and CAT-M1 devices.

There are somethings I don’t understand. Maybe someone here does.   

I created some listeners and parsers on a Linux machine. I configure 2 devices to connect to them. It is all quick and dirty coding, but I get the devices to connect and send data. 

On linux, I listen to TCP and I redirect incoming data to a file with
with the command 

```
netcat -k -l [port] > netcat.pcap
```


I start the listener with ```
tmux
``` so that I can detach from the session and keep the listener running headless
    
* It seems that **one** listener can only serve **one** device. Is that correct?  I am used to Apache Webserver, that can handle as many devices (browsers) that you want. But that is HTTP. If I point 2 devices to the same port, I get only the data from 1 device. Or am I doing something wrong / thinking in the wrong direction? 
       
* Another question. each device connects to it's own port. For current testing, that is good enough. (remember, I run the listener headless.) Yet it also seems the listener can get ‘corrupted’ or so. I then need to restart the netcat listener. Does anyone have any experience with this?

Thank you.

Adriaan

---

