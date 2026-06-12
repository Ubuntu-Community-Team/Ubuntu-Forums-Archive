---
title: "Proftpd log file"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Kenzo on 2009-06-15
I have set up Proftpd server and can connect to it fine. I have set up the client on a DVR to send files on event. SystemLog /var/log/secure shows the client is logging in okay. But files are not uploading. Tested loading files from a different ftp client and it works okay. I would like to see what the DVR client is doing after "Preparing to chroot to directory <directory>". 
What do I need to do to show this information - Do I need to add ExtendedLog or LogFormat to the proftpd.conf??

---

### Post by jonobr on 2009-06-15
I would recommend doing a wireshark or tcpdump trace on the ftp connection.

With wireshark you can view whats going on and given the clear nature of ftp you should be able to see everything thats happening.

I believe commands are issue on port 21 and data is done on port 20

So to see it logging in and sending passwords etc,

you could do the following

tcpdump -vvv port 21 -i any
This will show it to the terminal window


or

tcpdump -w ftp.pcap -s 1600 port 21 -i any

this will save to a file called  ftp.pcap which you can open in wireshark

---

### Post by Kenzo on 2009-06-16
Thanks for the info. This is what I got on port 21 - apart from the timestamps and ip it means zip to me.

20:51:52.769049 IP (tos 0x0, ttl 64, id 41857, offset 0, flags [DF], proto TCP (6), length 52) 192.168.1.200.39883 > server-desktop.local.ftp: ., cksum 0x2dd5 (correct), 63:63(0) ack 216 win 365 <nop,nop,timestamp 278586773 86027076>

I got nothing on port 20.  I did an upload using another ftp client and got nothing on port 20 for that either but the file loaded to the server okay. Using passive ports??

I was hoping there was something I could do to capture the info in a log file.  Like I said the SecureLog is showing the client is logging in to the server okay but I can't tell what is happening after that.  I'd like to be able to tell if its trying to send the file or not.

Don't know anything about Wireshark - will look it up. thanks

---

