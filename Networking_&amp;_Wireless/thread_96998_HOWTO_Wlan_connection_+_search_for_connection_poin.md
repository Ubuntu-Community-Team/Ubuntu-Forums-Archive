---
title: "HOWTO: Wlan connection + search for connection points automatically"
date: 2005-11-30
forum: Networking &amp; Wireless
---

### Post by pau on 2005-11-30
This took me a lot of headaches and troubles... I needed a long time 
to understand that the sequence of things is crucial to make it work... 
sad but true... I'm a poohead...

Therefore I am posting this here, because I think other people can be in the same situation like me and I'd like to help...

This is an extract of the page

[http://www.aei.mpg.de/~pau/amilo_1425_linux_en.html]("http://www.aei.mpg.de/~pau/amilo_1425_linux_en.html")

I will keep on improving the script there

Make first sure that your firewall is not enabled

```
ps aux |grep firestarter

If you find it, then

pkill -15 process_number
```

Another alternative, which is what I usually do, is to stop it

```
firestarter -p
```

When your connection wlan is running you can restart it again with

```
firestarter -s
```

(with wpa the firewall cannot be used unfortunately, I have to find out why)

Just in case of,

```
ps aux |grep dhcpcd
```

And you do the same, kill it like before (the name could be dhcpcd-bin,
dhclient3 or dhclient)

Well now you have to be sure the sequence of things you do is THIS one:

```
ifconfig eth0 down

ifconfig eth1 up

iwconfig eth1 essid "the_name_of_your_essid"
                                                                                                                                                                                                                                                                                                                                                                                                 
dhcpcd eth1
```

And that's it! 

If you are using a wpa encryption key, then it will look a bit different

```
ifconfig eth0 down

ifconfig eth1 up

iwconfig eth1 essid "your_network_name" key s:your_secret_key
                                                                                                                                                                                                                                                                                                                                                                                                 
dhcpcd eth1
```

One more thing: If you have a mac address filter on your router, be sure to 
upload the address of both devices, eth0 and wlan to it!

You can find the number like this:

```
ifconfig -a
```


The mac address is the number looking like this (underlined)

```
eth0      Link encap:Ethernet  HWaddr _00:13:3D:6F:65:1H_
          inet addr:192.168.2.100  Bcast:172.126.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:dff:fe1b:8017/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:181175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93962 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:268155966 (255.7 MiB)  TX bytes:5972294 (5.6 MiB)
          Interrupt:9 Base address:0xc800

eth1      Link encap:Ethernet  HWaddr _00:0T:19:5N:62:4Y_
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:ffdfd000-ffdfdfff


```

I wrote a small shell script to do automatically all this stuff and also to
look for connection points ("beams")

Since I don't feel like going through the whole thing each time I have to
look for a connection, I thought it'd a good thing to have a shell script 
doing this for me... which I call "Sense_fils.sh" (Catalan for "wireless") 
Well, here you have it. I assume your wlan interface is eth1 and your 
shell is zsh

```
#!/usr/bin/zsh

# Script "Sense_fils.sh". Stops firestarter, if running, also all possible dhcpcd
# connections and scans for possible networks, giving you the possibility of
# choising one of them and connect to it via wpa (ascii)
# Copyright Pau Amaro-Seoane and released under GPLv2:
# http://www.fsf.org/licensing/licenses/gpl.txt

# Check whether script talks to a person... errr... terminal

tty -s     && stdin_is_human=1
tty -s <&1 && stdout_is_human=1


firestarter -p

killall dhcpcd
killall dhcpcd-bin
killall dhclient3

ifconfig eth0 down
ifconfig eth1 up

# list of available wireless connections (aka beams)
beams=( $(iwlist eth1 scan | grep ESSID | cut -d":" -f 2 | sed 's/\"//g') )
n_beams=$#beams

# chose a "beam"
if [[ -n $stdin_is_human ]] && [[ -n $stdout_is_human ]]; then
    echo "Master, I've found the following beams to suit you:"
    for (( i=1; i<=n_beams; i++ )); do
        echo \ \ \[$i\] $beams[$i]
    done

    echo -n "        Which beam do you want (1-$n_beams) ?"
    read ibeam
    echo ""
    mybeam=$beams[$ibeam]
    echo " You selected \"$mybeam\"... Very good choice! (what are you doing tonight?)"
    echo -n " And... what about your password: "
    stty -echo # prevent password to be echoed
    read password
    stty echo
    echo ""
else
    ibeam=1
    ybeam=$beams[$ibeam]
    password=""
fi

iwconfig eth1 essid "$mybeam" key s:$password

dhcpcd eth1

echo "Congratulations Master. You are connected to \"$mybeam\". My pleasure"

```
The best thing to do is to put it into your local bin directory and run it as 
sudo or, better, in the sbin and call it as sudo (if you didn't set up a root
account yet):

```
chmod u+x Sense_fils.sh

sudo mv Sense_fils.sh /usr/sbin/

rehash
```
                                                                                                                                                                                                                                                                                                                                                                                                 
Well... some people can argue... Why don't you just use wifi-radar?!? And the answer is that wifi-radar (or the gnome-applet for network) doesn't succeed 
at connecting to the networks -at leat in my case- ... You're not forced to do things like I do... :rolleyes: 

bye,

Pau

---

