---
title: "Cannot redirect all (TCP) traffic through transparent socks5 proxy in Ubuntu 14.04"
date: 2015-08-18
forum: Networking &amp; Wireless
---

### Post by Daniyal_Javani on 2015-08-18
Hello
I try this to do that but cannot open any website. Could you please help me to redirect all (TCP) traffic through transparent socks5 proxy?
```

cd
sudo apt-get install iptables git-core libevent-2.0-5 libevent-dev 
git clone http://github.com/darkk/redsocks.git
cd redsocks/
make 
echo 'base{log_debug = on; log_info = on; log = "file:/tmp/reddi.log"; 
       daemon = on; redirector = iptables;}
       redsocks { local_ip = 127.0.0.1; local_port = 1080; ip = 127.0.0.1; 
       port = 1080; type = socks5; }' > redsocks.conf
./redsocks -c redsocks.conf 

sudo iptables -t nat -N REDSOCKS
sudo iptables -t nat -A REDSOCKS -d 0.0.0.0/8 -j RETURN
sudo iptables -t nat -A REDSOCKS -d 10.0.0.0/8 -j RETURN
sudo iptables -t nat -A REDSOCKS -d 127.0.0.0/8 -j RETURN
sudo iptables -t nat -A REDSOCKS -d 169.254.0.0/16 -j RETURN
sudo iptables -t nat -A REDSOCKS -d 172.16.0.0/12 -j RETURN
sudo iptables -t nat -A REDSOCKS -d 192.168.0.0/16 -j RETURN
sudo iptables -t nat -A REDSOCKS -d 224.0.0.0/4 -j RETURN
sudo iptables -t nat -A REDSOCKS -d 240.0.0.0/4 -j RETURN
sudo iptables -t nat -A REDSOCKS -p tcp -o eth0 -j DNAT --to 127.0.0.1:1080
sudo iptables -t nat -A OUTPUT -p tcp -j REDSOCKS

sudo iptables -t nat -I REDSOCKS -d _**67.220.203.130**_ -j RETURN #67.220.203.13 is my ip address
ssh -D 1080 my_user@mywebsite.com
```
I test the socks proxy with foxyproxy and works well.
If there is a easy way please tell me!

---

