---
title: "tcpdump - where does it save to?"
date: 2015-08-02
forum: Networking &amp; Wireless
---

### Post by jesse36 on 2015-08-02
I am following a tutorial that is using tcpdump with wireshark. I write the tcpdumb capture to a file with the command:

```
 sudo tcpdump -i 1 -w capture2_ubnt.pcap 
```

My problem is I cannot find where this new file is saved to? The tutorial skipped over this. They actually exported the file via ftp back to windows but didn't explain how. I have wireshark installed on ubuntu so I don't need to export it. I would like to open pcap file on Ubuntu but I just don't know where it is.

Thanks in advance.

---

### Post by Lars Noodén on 2015-08-02
It should save to the current directory, the one you were in when you ran tcpdump.  If you have doubts you can specify the full path of where you want it to end up.  

```
 sudo tcpdump -i 1 -w /home/jesse36/Documents/capture2_ubnt.pcap

```

Also you might want to specify the interface to monitor by name rather than number, such as eth0 or wlan0, just to make sure you are getting the right one.

---

### Post by jesse36 on 2015-08-02
Thanks Lars, well appreciated. I will give your advice a try.

---

