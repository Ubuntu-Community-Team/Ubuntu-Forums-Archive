---
title: "iptables causing high cpu"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by Jebajseti on 2011-04-18
Hi,

i have noticed that problem 2 days ago, restart helped but ofcourse iptable list was cleaned out. So today it happened again 20 min ago or so restarted server and its ok again.
But before i did that i runned htop and noticed that there was many processes runned by root iptables -l -v --line-numbers every process caused 3% of cpu usage, they appared like dont know... it was about 100% usage on both cores, then they dissapared soon and so on. Anyway how can i prevent that to happen on future? I have gameserver installed and this can be annoying to people if they lag untill i come and reboot whole server.

Hoping for solutions, regards

---

### Post by JKyleOKC on 2011-04-18
The iptables process is an integral part of the kernel, and is what implements the firewall functionality. The options that you report are to cause it to list all of its rules, and should not be getting run automatically. The first thing to do is to check your system log file at /var/log/syslog to find out, if possible, what is triggering this action.

The log file can be huge, so you may want to use commands like this to make the search easier (you can simply copy from this message and paste it into your terminal command line):```
cat /var/log/syslog|grep kernel >mylog
```Nothing will appear on the screen until you get the next prompt, but a file will be created in the directory from which you run this code. You can then examine the resulting "mylog" file with a text editor.

If you find a pattern of incidents repeated at regular intervals, the next place to look would be at the "cron" files to see if they contain an instruction to list the rules. I can't think of any valid reason for such an instruction to be there, but since you run gameserver (with which I'm not familiar) it's possible one might have been installed...

---

### Post by Jebajseti on 2011-04-18
well this is what i got mylog, and the server started to lag arround midnight atleast that time someone reported me. Log is in attachment

regards

---

### Post by JKyleOKC on 2011-04-18
The only thing there that looked at all suspicious to me was that your network interface eth0 goes into "promiscuous mode" every five minutes, for only a few seconds. This mode is often used by sniffers and port scanners, since it lets the network card accept all packets that appear on the wire, instead of only those that are addressed to it. However it's possible that this may be a normal action of gameserver; as I said earlier, I'm not at all familiar with that program.

What we need now is for someone else who knows gameserver to join in and help us determine what is happening. I don't think there's any direct connection between the five-minute switching, and the listing of iptables rules -- but if you can monitor htop or top for 10 to 15 minutes straight, and the listing process shows up at very regular 5-minute intervals, that would be cause for some concern. If someone did manage to plant a malicious script on your machine, it could be examining your firewall rules regularly. And since the process in question is running as root, such a script could do anything else its author wanted. Not at all good. However no need to be overly paranoid at this point, since it could in fact be part of gameserver's normal actions. Normally, malware scripts change things like htop and top to hide their presence completely, and destroy the syslog file. We'll just have to hope for an expert to chime in!

---

### Post by JKyleOKC on 2011-04-19
I did a bit more research this morning and found that virtualization software switches a network card to promiscuous mode, if the virtual machine uses bridging for its network connections. However the pattern that your log shows does not fit this possibility, since your log shows the switch happening regularly every five minutes, and lasting less than a minute each time. I do use virtualization, and my log shows the mode changes only a few times in 24 hours, and lasting for more than 6 hours in one instance where I was running a virtual machine for that long.

This begins to sound as if you could have a rootkit installed on your server; it's probably time to run a rootkit-detection utility!

---

### Post by Jebajseti on 2011-04-19
well when u told me every 5 minutes i got a clue what is that. But that cant be the fault, since my webserver is 2 months unchanged and what it does is only restart few servers and manualy reboot. Script that i'm runing every 5 minutes is a game script, which detect flood attempts and put them on fail2ban list. Also processes that were trigered every 10 seconds is not the fault of cron job which i have setted up for checking that.

Anyway here is the script, which was reported officialy for disabling flood attempts and is used every 5 minutes and not every 1-10 seconds.

```
#!/bin/bash

##################################################################################
##################################################################################
#                                                                                #
#  Q3-Engine-GetStatus-Flood-Fixer                                               #
#  Version 1.2                                                                   #
#                                                                                #
#                                                                                #
# Thanks to benny from Hirntot for the regexp                                    #
##################################################################################
########################       DESCRIPTION     ###################################
#                                                                                #
# This script try to get rid of the Q3-Engine getstatus-Abuse-Exploit            #
#                                                                                #
# About the exploit                                                              #
#                                                                                #
# This exploit use the getstatus udp query command with a spoofed sender         #
# adress. This 14 byte long command enganges the gameserver engine to            #
# respond the whole status of the gameserver ( > ~600 bytes on empty server)     #
# This amplification is visible if you use a tool like vnstat (vnstat -l)        #
# The outgoint traffic exceeds the incoming traffic with a faktor > 3            #
#                                                                                #
#                                                                                #
# About the script                                                               #
# This script capture the count of tcp packets set in config and search for      #
# answered getstatus queries. For any requesting IP adress the count of          #
# those packets is compared to the defind limit.                                 #
# If the limit is broken by an IP adress, the access for this IP will ne denied  #
# with iptables by adding a drop rule.                                           #
#                                                                                #
# Configuration                                                                  #
#                                                                                #
# By default, the script don`t need any configuration                            #
# The default values                                                             #
#                                                                                #
# CAPTURETIME=3                                                                  #
# MAXPERSECONDS=2                                                                #
# will enforces drops in the case that:                                          #
#                                                                                #
# Each IP which requests more than 2 getstatus respones per second,              #
# averaged over 3 seconds                                    #
#                                                                                #
# Requirements                                                                   #
#                                                                                #
# This script use a few open source tools to offence against this attacks        #
# tcpdump - capture incoming packets: http://www.tcpdump.org/                    #
# iptables - the most used linux firewall (packet filter)                        #
# GNU-tools - grep, cat                                                          #
#                                                                                #
# THIS SCRIPT COMES WITH NO WARRANTY! USE IT AT YOUR OWN RISK ONLY!              #
#                                                                                #
##################################################################################
######################       CONFIGURATION      ##################################
##################################################################################

. /etc/profile
CAPTURETIME=5
MAXPERSECONDS=2

##################################################################################
##################################################################################
##################################################################################

captsec=$CAPTURETIME
mylimit=$MAXPERSECONDS
cntout=file_cntout
tmpout=file_tmpout
tmpout2=file_tmpout2
tmpout3=file_tmpout3
banlist=file_bans

#fix: 31.01.2011 21:45
touch $banlist
#

MYIFS=$IFS
IFS="
"


rm $cntout 2>/dev/null
rm $tmpout 2>/dev/null
rm $tmpout2 2>/dev/null
rm $tmpout3 2>/dev/null



tcpdump -f -c 100000 -A >$tmpout 2>$cntout &
pid=$!
sleep $captsec
kill $pid
sleep 1

maxcnt=$((mylimit*captsec))
grep -B2 Respon $tmpout | grep UDP | awk '{print $5}' | cut -d '.' -f 1,2,3,4 > $tmpout3

allIPs=`grep -B2 Respon $tmpout | grep UDP | awk '{print $5}' | cut -d '.' -f 1,2,3,4 | sort -u`
for ip in $allIPs
do

IPCNT=`grep "$ip" $tmpout3 | wc -l`
#PORTS=`grep -B2 Respon $tmpout | grep UDP | cut -d "." -f 4 | cut -d " " -f 1 | sort -u`
PORTS=`grep -B2 Respon file_tmpout | grep UDP |awk '{print $3}' | perl -e 'while (<STDIN>) {print "$1\n" if ($_ =~ /\.(\d+)$/)}' | sort -u`
if [ $IPCNT -gt $maxcnt ]
then
for PORT in $PORTS
do
ts=`date --utc +%s`
rps=$((IPCNT/captsec))
tshr=`date --utc --date "1970-01-01 $ts sec" "+%Y-%m-%d %T"`
out="$ts $ip $PORT $IPCNT = $rps ReqPerSec banned $tshr"
iptables -A INPUT -p udp -s $ip --dport $PORT -j DROP
echo $out >>$banlist
done
else
DEBUGOUT="no ban"
fi
done
####AUTO-UNBAN

LINES=`cat $banlist | sort -u`
for LINE in $LINES
do
LIP=`echo $LINE | awk '{print $2}'`
LPORT=`echo $LINE | awk '{print $3}'`

LCNT=`grep "$LIP" $tmpout | wc -l`
if [ "$LCNT" != "0" ]
then
DEBUGOUT="No release $LIP $LPORT"
else
#RELEASE
IPTBLN=`iptables -L -v --line-numbers | grep "$LIP" | grep "$LPORT" | awk '{print $1}'`
CHECK=`iptables -L -v --line-numbers | grep "$LIP" | grep "$LPORT" | wc -l`
DEBUGOUT="RELEASE $LIP $LPORT BUG"
#echo "iptables -L -v --line-numbers \| grep \"$LIP\" \| grep \"$LPORT\" "

#echo "IPTBLID $IPTBLN CHECK $CHECK"
if [ "$CHECK" != "0" ]
then
iptables -D INPUT $IPTBLN
DEBUGOUT="RELEASE $LIP $LPORT"
grep -v "$LIP" $banlist > tmp001
mv tmp001 $banlist
fi


#echo $DEBUGOUT
fi
done




rm $tmpout3 2>/dev/null
rm $cntout 2>/dev/null
rm $tmpout 2>/dev/null
rm $tmpout2 2>/dev/null
IFS=$MYIFS


```

p.s. like i said, there is no problem with server now 2 days for example... then it sudenly starts laging coz of cpu usage. If i restart its ok for day or 2

---

### Post by bodhi.zazen on 2011-04-19
Well, it is easy to check =)

Stop fail2ban and stop the script, see if they problem then resolves.

If so, then it is either the script or fail2ban, enable one at a time, then both together.

---

### Post by JKyleOKC on 2011-04-19
> **Jebajseti said:**
> well when u told me every 5 minutes i got a clue what is that. But that cant be the fault, since my webserver is 2 months unchanged and what it does is only restart few servers and manualy reboot. Script that i'm runing every 5 minutes is a game script, which detect flood attempts and put them on fail2ban list.  
```
####AUTO-UNBAN

LINES=`cat $banlist | sort -u`
for LINE in $LINES
do
LIP=`echo $LINE | awk '{print $2}'`
LPORT=`echo $LINE | awk '{print $3}'`

LCNT=`grep "$LIP" $tmpout | wc -l`
if [ "$LCNT" != "0" ]
then
DEBUGOUT="No release $LIP $LPORT"
else
#RELEASE
[COLOR="Red"]IPTBLN=`iptables -L -v --line-numbers | grep "$LIP" | grep "$LPORT" | awk '{print $1}'`
CHECK=`iptables -L -v --line-numbers | grep "$LIP" | grep "$LPORT" | wc -l`
[/COLOR]DEBUGOUT="RELEASE $LIP $LPORT BUG"
#echo "iptables -L -v --line-numbers \| grep \"$LIP\" \| grep \"$LPORT\" "

#echo "IPTBLID $IPTBLN CHECK $CHECK"
if [ "$CHECK" != "0" ]
then
iptables -D INPUT $IPTBLN
DEBUGOUT="RELEASE $LIP $LPORT"
grep -v "$LIP" $banlist > tmp001
mv tmp001 $banlist
fi
```

p.s. like i said, there is no problem with server now 2 days for example... then it sudenly starts laging coz of cpu usage. If i restart its ok for day or 2I've edited your script down to just the relevant part, and highlighted in red the two lines that are causing the iptables listing action. They seem to be absolutely central to the action of your script, to unban offenders after a while.

Perhaps using the original fail2ban scripts would remove the problem, but if you need to stay with this script, the place to look is in the variable "tmpout" which is controlling this undesired action. If tmpout remains empty, the action does not happen; if it doesn't, you get lagged. Perhaps someone is doing a DDOS on you and it takes the 10 minutes or so to trigger this "autounban" code...

---

