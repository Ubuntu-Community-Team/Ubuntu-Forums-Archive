---
title: "VPN through Cable modem in Feisty [Israel]"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by kripkenstein on 2007-04-20
I believe I have fixed a problem for me, so I'm posting it here in hopes it will help other people (who do a search for similar terms).

Problem: I have cable internet access, and my ISP is available through a VPN (this is because of legal issues with the cable companies in Israel, silly really). Anyhow, in 5.10, 6.06 and 6.10 I used a standard script to connect, and it worked (the script is available from the Netvision option in the welcome.hot.net.il site, with minor modifications for my ISP). But in Feisty 7.04, it worked only 10% of the time. I would get (in the syslog) errors like wrong password, or network is unavailable, very odd. Also the DHCP leases would expire fairly quickly.

Anyhow, after much fiddling, I think I found the issue. It is probably related to one of the new networking options in Feisty - Network-Manager and Avahi - that is my guess at least. Anyhow, I noticed that the timing had changed for the various actions in the connection script (ifup, ifdown). So I added a "sleep 3" after *each* command there, to prevent timing or 'race' conditions. And this seems to have worked, surprisingly enough, now the script works ok.

My theory is that there is more going on with Feisty's networking than previous versions, and it just takes more time to 'settle down'. So waiting after each command helps out. Of course I could be totally wrong ;) but it does work, for now at least.

---

### Post by barmazal on 2007-04-20
same story, the previous version of application  i had from my ISP was asking to install pptp-linux using synoptic. Then we needed to run installer and set our username / password details.

for now, the method does not work even if i copy pptp-linux to usr/sbin


can you guys specify what soft of change you made in pptp-linux area so maybe we will find a way to figure that out.

I can post source code of installer we had in case anyone spots error for Festy

```
#!/bin/sh
#Made by Marcelo A.

# Must be root
if test "$UID" != 0 ; then
 echo -e "This script must be run as root.\nType in root password, please."
 exec su -c "DISPLAY=$DISPLAY $0"
 exit 1
fi
   
# Must have pppd
if [ ! -x "`which pppd`" ] ; then
    echo "Oops, I can't execute the program pppd.  You"
    echo "must install the PPP software suite, version 2.3.10 or later."
    exit 1
 fi

# If pptp or pptp-linux aren't found ,abort installation
if ! [ -x /usr/sbin/pptp-linux -o -x ./pptp-linux -o -x "`which pptp`" ] ; then
    echo "Can't execute the program pptp. You should" 
    echo "install the pptp linux client that comes with your distribution ,version 1.1.0 or later"
    echo ""
    echo "NOTE! ,Mandrake users should install the package pptp-adsl *NOT* pptp-linux!"
    echo ""
    echo "If all fails and your distro dosen't come with a pre-compiled pptp" 
    echo "client, you could try the one in ./scripts , just copy it"
    echo "to the parent directory .. or /usr/sbin"
  
  exit 1
fi

if ! pptp 2>&1 |grep "nolaunchpppd" 2>&1 > /dev/null ; then
 LINUXPPTP="./scripts/pptp-linux"
   echo "Your pptp client is old, consider upgrading ppp and pptp to the latest version..."
   echo "Using pptp-linux binary..."
fi
     
mkdir -p /usr/sbin
for i in ip-up-bak ; do 
        if [ ! -x /etc/ppp/$i ] ; then 

           if [ -x /etc/ppp/ip-up ] ; then

echo "Backing up /etc/ppp/ip-up and /etc/ppp/ip-down to ip-up-back and ip-down-bak"
               cp -d /etc/ppp/ip-up /etc/ppp/ip-up-bak
               cp -d /etc/ppp/ip-down /etc/ppp/ip-down-bak
               install -c -m 755 ./scripts/ip-* /etc/ppp ; 
           fi
        else 
                echo "NOT overwriting existing /etc/ppp/$i ip-down-bak" ;
                echo "Consider running Uninstall before Reinstalling again.." 
        fi 
done
	
#Nasty hack that checks if /usr/sbin is writable 
#case it isn't, it will place cable-s* files in current directoy;
#solves the issue with live-cds where /usr/sbin is readonly
for i in ./scripts/cable-s* ; do
  if ( : > /usr/sbin/1234a ) &>/dev/null ; then
install -c -m 755 $i $LINUXPPTP /usr/sbin
rm -f /usr/sbin/1234a
  else
install -c -m 755 $i $LINUXPPTP ./
  fi     
done 

mkdir -p /etc/ppp

for i in pptp.conf ; do 
        if [ ! -f /etc/ppp/$i ] ; then 
                install -c -m 644 ./config/$i /etc/ppp 
        else 
                echo "NOT overwriting existing /etc/ppp/$i" 
                install -c -m 644 ./config/$i /etc/ppp/$i-1.0 
        fi 
done
									
if [ -f /etc/redhat-release ] ; then 
        echo "Looks like a Red Hat system; installing /etc/rc.d/init.d/cable" 
        mkdir -p /etc/rc.d/init.d 
        install -c -m 755 ./scripts/cable-init /etc/rc.d/init.d/cable 
fi
if [ -f /etc/turbolinux-release ] ; then 
        echo "Looks like a TurboLinux system; installing /etc/rc.d/init.d/cable" 
        mkdir -p /etc/rc.d/init.d 
        install -c -m 755 ./scripts/cable-init-turbolinux /etc/rc.d/init.d/cable 
fi
if [ -f /etc/SuSE-release ] ; then 
        echo "Looks like a SuSE Linux system; installing /etc/rc.d/init.d/cable" 
        mkdir -p /etc/rc.d/init.d 
        install -c -m 755 ./scripts/cable-init-suse /etc/rc.d/init.d/cable 
fi
echo ""
exec sh ./scripts/cable-setup

```

---

### Post by kripkenstein on 2007-04-20
> **barmazal said:**
> 
can you guys specify what soft of change you made in pptp-linux area so maybe we will find a way to figure that out.


Hmm, it seems the important stuff in your script is the last line, "exec sh ./scripts/cable-setup". That script might have important commands.

Anyhow, I'm glad to post what I have, but it may be too specific for my (country /) networking / ISP, (Israel /) Cable company / Netvision. Anyhow, hope this helps. Let me know how it goes.

```

#!/bin/bash

USERNAME="$1"
IFACE="$2"

ifdown $IFACE
sleep 3

ifup $IFACE
sleep 3

CABLEGW=$(grep routers /var/lib/dhcp3/dhclient.eth0.leases | tail -n 1 | cut -d ";" -f1 | cut -d "t" -f3 | cut -d "o" -f4 | cut -d ' ' -f2)

route add -host cable.netvision.net.il gw $CABLEGW
sleep 3

#./pptp-linux or pptp?
./pptp-linux cable.netvision.net.il debug noauth user $USERNAME mtu 1460 mru 1460 defaultroute &
sleep 8

NEWGW=$(ifconfig ppp0 | grep inet | cut -d":" -f3 | tail -1 | cut -d" " -f1)

/sbin/route add default gw $NEWGW
sleep 3

/sbin/route del default gw $CABLEGW
sleep 3

echo "nameserver 194.90.1.5" > /etc/resolv.conf
echo "nameserver 212.143.212.143" >> /etc/resolv.conf
sleep 3

```

To run it, do ```
./script_name USERNAME eth0
``` (or whatever interface you want other than eth0)

---

### Post by kripkenstein on 2007-04-20
Two more things:

1. I am using a 'pptp-linux' available from the ISP, Netvision. This is, I believe, an older version of the one in the repos. The repos one doesn't seem to work for me. I can give you the older one if you want.

2. You need to set up the /etc/ppp/pap-secrets and /etc/ppp/chap-secrets files with your username and password, etc., for the script to work.

---

### Post by barmazal on 2007-04-20
ops wrong file pasted

this is cable-setup file

```
#!/bin/bash
#Made by Marcelo A.

# Set to "C" locale so we can parse messages from commands
LANG=C
export LANG

CONFIG=/etc/ppp/pptp.conf
USER=""
ETH=""
ME=`basename $0`
# Protect created files
umask 077
copy() {
    cp $1 $2
    if [ "$?" != 0 ] ; then
       echo "*** Error copying $1 to $2"
       echo "*** Quitting."
       exit 1
    fi
}

# Must be root
if [ "`id -u`" != 0 ] ; then
    echo "$ME: You must be root to run this script" >& 2
    exit 1
fi

# Prototype config file must exist
if [ ! -r "$CONFIG" ] ; then
    echo "Oh, dear, I don't see the file '$CONFIG' anywhere.  Please"
    echo "re-install the client."
    exit 1
fi

. $CONFIG
  
echo "Welcome to the cable connection setup."
echo "Please enter some information:"

while [ true ] ; do
    echo ""
    echo "USER NAME"
    echo ""
    echo -n ">>> Enter your user name (default $USER): "
    read U

    if [ "$U" = "" ] ; then
        U="$USER"
    fi

    # Under Linux, "fix" the default interface if eth1 is not available
    if test `uname -s` = "Linux" ; then
        ifconfig $ETH > /dev/null 2>&1 || ETH=eth0
    fi
    echo ""
    echo "INTERFACE"
    echo ""
    echo ">>> Enter the Ethernet interface connected to the Cable modem"
    echo "For Linux, it will be ethn, where 'n' is a number."
    echo -n "(default $ETH): "
    read E

if [ "$E" = "" ] ; then
        E="$ETH"
    fi

    echo ""
    echo "SERVER ADDRESS"
    echo ""
    echo ">>> Enter the Server address of your ISP."
    echo -n "(default $SERVERADDR): "
    read S
   if [ "$S" = "" ] ; then
         S="$SERVERADDR"
   fi	
   
    echo ""
    echo "DNS"
    echo ""
    echo "Please enter the IP address of the primary DNS server."
    echo "If you want the server to automatically provide you the addresses',"
    echo "enter 'server' (all lower-case) here."
    echo "If you just press enter, I will assume you know what you are"
    echo "doing and not modify your DNS setup."
    echo -n ">>> Enter the DNS information here: "
    
    read DNS1

    
    if [ "$DNS1" != "" ] ; then
        if [ "$DNS1" != "server" ] ; then
            echo "Please enter the IP address of your ISP's secondary DNS server."
            echo "If you just press enter, I will assume there is only one DNS server."
            echo -n ">>> Enter the secondary DNS server address here: "
             read DNS2
        fi
    fi
													    

    while [ true ] ; do
        echo ""
        echo "PASSWORD"
        echo ""
        stty -echo
        echo -n ">>> Please enter your password:    "
        read PWD1
        echo ""
        echo -n ">>> Please re-enter your password: "
        read PWD2
        echo ""
        stty echo
        if [ "$PWD1" = "$PWD2" ] ; then
            break
        fi

        echo -n ">>> Sorry, the passwords do not match.  Try again? (y/n)"
        read ANS
        case "$ANS" in
            N|No|NO|Non|n|no|non)
                echo "OK, quitting.  Bye."
                exit 1
        esac
    done
   
   echo ""
   echo "** Summary of what you entered **"
   echo ""
   echo "Ethernet Interface: $E"
   echo "User name:          $U"

    if [ "$DNS1" != "" ] ; then
        if [ "$DNS1" = "server" ] ; then
            echo "DNS addresses:      Supplied by ISP's server"
        else
            echo "Primary DNS:        $DNS1"
            if [ "$DNS2" != "" ] ; then
                echo "Secondary DNS:      $DNS2"
	    fi
         fi
     else
         echo "DNS:                Do not adjust"
     fi
         echo ""
	 while [ true ] ; do
	 echo -n '>>> Accept these settings and adjust configuration files (y/n)? '
	 read ANS
	 case "ANS" in
	     Y|y|yes|Yes|oui|Oui)
	         ANS=y
	         ;;
	     N|n|no|No|non|Non)
	         ANS=n
	         ;;
	 esac
	 if [ "$ANS" = "y" -o "$ANS" = "n" ] ; then
	     break
	 fi
     done
     if [ "$ANS" = "y" ] ; then
         break
     fi
 done

# Adjust configuration files.  First to $CONFIG
copy $CONFIG $CONFIG-bak
if [ "$DNS1" = "server" ] ; then
    DNSTYPE=SERVER
    DNS1=""
    DNS2=""
    PEERDNS=yes
else
    PEERDNS=no
    if [ "$DNS1" = "" ] ; then
        DNSTYPE=NOCHANGE
    else
        DNSTYPE=SPECIFY
    fi
fi
# Where is pppd likely to put its pid?
if [ -d /var/run ] ; then
    VARRUN=/var/run
else
    VARRUN=/etc/ppp
fi

			
sed -e "s&^USER=.*&USER='$U'&" \
    -e "s&^ETH=.*&ETH='$E'&" \
    -e "s&^SERVERADDR=.*&SERVERADDR='$S'&" \
    -e "s/^DNSTYPE=.*/DNSTYPE=$DNSTYPE/" \
    -e "s/^DNS1=.*/DNS1=$DNS1/" \
    -e "s/^DNS2=.*/DNS2=$DNS2/" \
    -e "s/^PEERDNS=.*/PEERDNS=$PEERDNS/" \
    < $CONFIG-bak > $CONFIG

if [ $? != 0 ] ; then
    echo "** Error modifying $CONFIG"
    echo "** Quitting"
    exit 1
fi

echo "Adjusting /etc/ppp/pap-secrets and /etc/ppp/chap-secrets"
if [ -r /etc/ppp/pap-secrets ] ; then
    echo "  (But first backing it up to /etc/ppp/pap-secrets-bak)"
    copy /etc/ppp/pap-secrets /etc/ppp/pap-secrets-bak
else
    cp /dev/null /etc/ppp/pap-secrets-bak
fi
if [ -r /etc/ppp/chap-secrets ] ; then
    echo "  (But first backing it up to /etc/ppp/chap-secrets-bak)"
    copy /etc/ppp/chap-secrets /etc/ppp/chap-secrets-bak
else
    cp /dev/null /etc/ppp/chap-secrets-bak
fi

egrep -v "^$U|^\"$U\"" /etc/ppp/pap-secrets-bak > /etc/ppp/pap-secrets
echo "\"$U\"   *       \"$PWD1\"       *" >> /etc/ppp/pap-secrets
egrep -v "^$U|^\"$U\"" /etc/ppp/chap-secrets-bak > /etc/ppp/chap-secrets
echo "\"$U\"   *       \"$PWD1\"       *" >> /etc/ppp/chap-secrets

echo ""
echo ""
echo ""
echo "Congratulations, it should be all set up!"
echo ""
echo "Type: 'cable-start'  - to bring up your CABLE link"
echo "      'cable-stop'   - to bring it down"
echo "      'cable-status' - to see the link status."
exit 0

```

---

### Post by kripkenstein on 2007-04-20
> **barmazal said:**
> ops wrong file pasted

this is cable-setup file


Looks like it sets up the config files. Would have come in handy for me, I had to learn how to set them up by hand :)

Anyhow, the script I pasted should connect ok, if you have a correctly set-up pap-secrets and chap-secrets, which your script can apparently do (if not, doing it yourself is very simple, just adding a single line to each).

---

### Post by barmazal on 2007-04-20
kripkenstein, the point is why there is no pptp-linux in synaptic like before. this script does what i need do to manually.

---

### Post by kripkenstein on 2007-04-20
> **barmazal said:**
> kripkenstein, the point is why there is no pptp-linux in synaptic like before. this script does what i need do to manually.

Are you sure you don't have pptp-linux in synaptic? I see it there. Also shown in
```

%apt-cache search pptp-linux
pptp-linux - Point-to-Point Tunneling Protocol (PPTP) Client

```

Perhaps you need to refresh your package list from the repos, or enable universe/multiverse?

---

### Post by barmazal on 2007-04-20
yes, sorry the layout of it changed a bit and i was looking for installed modules only. pptp-linux on. I do the installer and all goes smooth but when i run sudo cable-start which soppesedly should turn my connection on it does show new ip and that authentication is right but it does not surf the web,  though i can get to hot.co.il drivers page whether i'm though lan card or usb (previous ubuntu was not able to connect to drivers page via usb)

don't know what the problem and still no answer from my ISP support.

---

### Post by kripkenstein on 2007-04-20
Well, you can try the script I gave in order to connect, but it is very 'inelegant', sadly.

When you hear back from your ISP, please update me, I am curious.

---

### Post by barmazal on 2007-04-20
connected! now from Ubuntu, it was my mistake durring the installation i missed one part

---

### Post by kripkenstein on 2007-04-20
Ok, cool.

Unrelated to my original issue, then, I guess.

---

### Post by Quibly on 2007-04-26
I had the exact same problem - (ISP 012, with HOT), I screwed around a little with the network manager thing (didnt do anything too serious), and not it suddenly works. This is the first time that I successfully connected. I hope that next time I try to connect it will also work...

---

