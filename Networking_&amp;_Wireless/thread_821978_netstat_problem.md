---
title: "netstat problem"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by suxxor on 2008-06-07
i can`t get the whole output from command "netstat  -p"
this is all what shows me in terminal :
 
 
this is all what shows me in terminal :
 

 
this is the whole content in terminal after execute of the command
 
and the initial connections which shows me for small interval of time disappeared

---

### Post by jetsam on 2008-06-07
If all you want to see is internet connections,
```
sudo netstat -utap
```
..will show just listening and established tcp and udp (i.e. internet) connections and not the internal Unix sockets.  

Also, if you're using the gnome terminal, you can increase the amount of info that the scroll back buffer holds by opening a terminal and increasing the value in **edit menu-->profiles-->default profile-->edit button-->scrolling tab-->scrollback**.  Setting it to 1000 or so should be enough to hold the entire **netstat -p** process list.  

There's a gagillion ways (well, more than two, anyway) to deal with long output.  
```
netstat -p **>** my-netstat-list.txt
```
Will send the output to a file called **my-netstat-list.txt** in the current working directory.  Then you can open it in a text editor to view it.  Careful with the > redirector though: it will overwrite the file **my-netstat-list.txt** without so much as a beep to warn you that's what it's doing.

---

### Post by suxxor on 2008-06-08
10x a lot for help

---

### Post by suxxor on 2008-06-08
could you tell me some tool for getting MAC addresses from IP ,except the arp

---

### Post by jetsam on 2008-06-08
Nmap can do it if the machine is on the local LAN segment.
```
sudo nmap -n -sP **<ip address>**
```

Each router hop strips and replaces the mac address on a packet, so there's no way to find a remote system's mac address.

---

