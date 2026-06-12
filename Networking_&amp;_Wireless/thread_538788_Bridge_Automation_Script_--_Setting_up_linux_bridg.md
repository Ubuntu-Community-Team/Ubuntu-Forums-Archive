---
title: "Bridge Automation Script -- Setting up linux bridges. With Rateshaping"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by Pugss on 2007-08-30
I needed to rate shape traffic to three routers with out taking an IP address so I came up with this script and thought the community could find it useful.

It must be run as root  /usr/local/bridge other than that you need tc and ebtables - you don't have to rebuild the kernal to install them (or at least I didn't have to). 

Just copy it in to /usr/local/bridge make it run-able (chmod o+x bas.sh) then run it ./bas.sh

Hit configure enter your info then add a user to the rate shaping and your good to go. 
You don't have to set up rate shaping if it is not need.
According to David Stahr it can run as many as 500 users on a very low end box. 

I also like to use ntop with it but you can look that up on your own.

```

#!/bin/bash
#------------------------------------------------------------------------------
# This is an attempt to automate The configuration of a rating shaping        |
#bridge. Thanks to Dave Stahr for the config files and great info             |
#http://ebtables.sourceforge.net/examples/example5.html                       |
# Bridge Automation Script 						      |
# By Pugss --- email Laethdar {aT} Gmail.com                                  |
# Version 1.0 								      |
#------------------------------------------------------------------------------

#------------------------------------------------------------------------------
# You need TC and ebtables for this to work they can be gotten via apt-get.   |
# Pleaase note this is not a NAT so your ISP will have to give you as many    |
# address as you have Routers - you could just use computers and leave out the|
# routers but is not recomended. We are also using cbq.                       |
#------------------------------------------------------------------------------


#------------------------------------------------------------------------------
#------------------------------My Set Up---------------------------------------
#------------------------------------------------------------------------------
#                           Cable Modem                                       |
#                                |                                            |
#                             BRIDGE (ubuntu 7.04 server)                     |
#                                |                                            |
#                             SWITCH  (5 port, connect bridge to uplink port  |
#                             /  |    \                                       |
#(Use these MACs)       Linksys D-Link  Belkin (Routers connect via WAN port) |
#                          |     |        |                                   |
#                      Computers---Computers                                  |
#                                                                             |
#-----------------------------------------------------------------------------|


#------------------------------------------------------------------------------
# X is the state basicly you don't need to worry about this ever.             |
# CONFIGFILE is where the data from the script is stored                      |
# RATEFILE is where the information reguarding customer rates are             |
# stored.                                                                     |
#------------------------------------------------------------------------------

CONFIGFILE=br1.conf
RATEFILE=rateshape1.sh
X=1

#-------------------------------------------------------------------------------
# This function draws the menu then reads the input for the case above         |
#-------------------------------------------------------------------------------

function menu {
	clear
	echo "####################################################"
	echo "##           Bridge Automation Script             ##"
	echo "####################################################"
	echo "####################################################"
	echo "# 1.)Configure The Bridge                          #"
	echo "# 2.)Start the Bridge                              #"
	echo "# 3.)Stop the bridge                               #"
	echo "# 4.)Rateshape it                                  #"
	echo "# 5.)Rateshape off                                 #"
	echo "# 6.)Rateshape Restart                             #"
	echo "# 7.)Entire restart of bridge and rateshaper       #"
	echo "# 8.)Rateshape show                                #"
	echo "# 9.)Add customer to Rate shape                    #"
	echo "# 10.)Disply "$CONFIGFILE"                              #"
	echo "# 11.)Remove "$CONFIGFILE" "$RATEFILE"                #"
	echo "# 12.)EXIT                                         #"
	echo "####################################################"
	echo "Please make your selection (1-12)"
	echo "Note- if this the first time running this please select configure"
	echo
	read CHOICE
}

#------------------------------------------------------------------------------
# This function displays the current variables loaded in memory not in the    |
# config file this is mainly a debugging feature.                             |
#------------------------------------------------------------------------------

function displayConf {
	
	echo $MODEM
	echo $INSIDE
	echo $BRNAME
	echo $COUNT
	sleep 1
}

#------------------------------------------------------------------------------
# This is called upon every return to the top to make sure we always have     |
# fresh data. It basicly looks for $CONFIGFILE and if it dosen't find         |
# CONFIGFILE it warns but dosen't create $CONFIGFILE.                         |
# This also sets the count variable to one if it less than on.                |
# It only looks in /usr/local/bridge so make sure the script is               | 
# ran from there.                                                             |
#------------------------------------------------------------------------------

function readConf {
	if [ -f $CONFIGFILE ]
		then 
		. $CONFIGFILE
		MODEM="$MODEM"
		INSIDE="$INSIDE"
		BRNAME="$BRNAME"
		COUNT="$COUNT"
		sleep 1
			if [ $COUNT -lt "1" ]
			then
			let COUNT=1
			echo $COUNT
			sleep 1
			echo "COUNT="$COUNT>>$CONFIGFILE 
			fi
		else
			echo "You need to be in /usr/local/bridge or"
			echo "make sure you have ran the configuration"
			echo "Or it is first run"
		sleep 1
	fi
}

#------------------------------------------------------------------------------
# This gets the info on the bridge set up and writes it to $CONFIGFILE.       |
# It then calls writeRateShape                                                |
#------------------------------------------------------------------------------ 

function writeConfig {
	echo
	echo "To add customers to please use the menu option"
	echo " " 
	read -p "Enter the interface Connected to the outside eg eth1--> " MODEM
	echo " "
	read -p "Enter the interface going to your equpment eg eth2--> " INSIDE
	echo " "	
	read -p "Enter what you want to call your bridge eg br0--> " BRNAME
	let $COUNT=1 
	echo "MODEM="$MODEM >$CONFIGFILE
	echo "INSIDE="$INSIDE >>$CONFIGFILE
	echo "BRNAME="$BRNAME >>$CONFIGFILE
	echo "COUNT=1">>$CONFIGFILE
	writeRateShape
}

#------------------------------------------------------------------------------
# This brings the bridge up on the system                                     |
#------------------------------------------------------------------------------
function bridgeUp {
	ifdown $MODEM
	ifdown $INSIDE
	ifconfig $MODEM 0.0.0.0 up
	ifconfig $INSIDE 0.0.0.0 up
	brctl addbr $BRNAME
	brctl addif $BRNAME $MODEM
	brctl addif $BRNAME $INSIDE
	ifconfig $BRNAME up
	
}

#------------------------------------------------------------------------------
# Does just what the name says it shuts down the bridge and the adapters      |
#------------------------------------------------------------------------------

function bridgeDown {
	ifdown $MODEM
	ifdown $INSIDE
	ifconfig $BRNAME down
	brctl delbr $BRNAME
	
}

#------------------------------------------------------------------------------
# This writes the top of the rate shape file it includes and example it also  |
# sets up the top qdisc for TC. We are using cbq here so it set that up as    |
# well. This also give the owner of $RATEFILE run privleges                   |
# it should be root but i don't have the UID check figured out yet            |
#                                                                             |
# PS I will soon be changeing $RATEFILE to a variable at the top so it        |
# is ease to change if you need a few configs.                                |
#------------------------------------------------------------------------------

function writeRateShape {
	echo "#!/bin/bash">$RATEFILE
	echo "TC=/sbin/tc">>$RATEFILE
	echo "EBTABLES=/sbin/ebtables">>$RATEFILE
	echo "$TC qdisc add dev "$MODEM" root handle 1:0 cbq bandwidth 100Mbit avpkt 1000 mpu 64">>$RATEFILE
	echo "$TC qdisc add dev "$INSIDE" root handle 1:0 cbq bandwidth 100Mbit avpkt 1000 mpu 64">>$RATEFILE
	echo "#This is a template if you want to edit this file manuly">>$RATEFILE
	echo "#If you edit this manuly and do use my script please be sure to edit the $CONFIGFILE and increase the counter vairable"
	echo "#Customer A">>$RATEFILE
	echo "#MAC Address: 00:0D:BD:A4:D6:54">>$RATEFILE
	echo "#800kbps download speed">>$RATEFILE
	echo "#${TC} class add dev eth0 parent 1:0 classid 1:1 cbq rate 800KBit allot 1514 prio 1 avpkt 1000 bounded">>$RATEFILE
	echo "#${TC} filter add dev eth0 parent 1:0 protocol ip handle 1 fw flowid 1:1">>$RATEFILE
	echo "#${EBTABLES} -A FORWARD -d 00:0D:BD:A4:D6:54 -j mark --set-mark 1 --mark-target ACCEPT">>$RATEFILE
	echo "#64kbps upload speed">>$RATEFILE
	echo "#${TC} class add dev eth1 parent 1:0 classid 1:1 cbq rate 64KBit allot 1514 prio 1 avpkt 1000 bounded">>$RATEFILE
	echo "#${TC} filter add dev eth1 parent 1:0 protocol ip handle 1 fw flowid 1:1">>$RATEFILE
	echo "#${EBTABLES} -A FORWARD -s 00:0D:BD:A4:D6:54 -j mark --set-mark 1 --mark-target ACCEPT">>$RATEFILE
	echo " "
	echo " "
	chmod o+x $RATEFILE
}

#------------------------------------------------------------------------------
# This just runs the $RATEFILE script that we just made if their is no one    |
# added to the $RATEFILE it SHOULDN'T rate shape anything                     |
#------------------------------------------------------------------------------

function rateShapeOn {
	. ./$RATEFILE	
}

#------------------------------------------------------------------------------
# This shuts down the top qdiscs in TC thus killing the rate shaping          |
#------------------------------------------------------------------------------

function rateShapeOff {
	${EBTABLES} -F
	$TC qdisc del dev $MODEM root
	$TC qdisc del dev $INSIDE root	
}

#------------------------------------------------------------------------------
# This restarts ONLY the rateshaper, we need to restart every time we add a   |
# a user to ratehape.sh so that they get rate shaped and not just wrote the   |
# file.                                                                       |
#------------------------------------------------------------------------------

function rateShapeRestart {
	echo "restarting Rate shaping only, this is called everytime is a customer is added"
	rateShapeOff
	. ./$RATEFILE	
}

#------------------------------------------------------------------------------
# This function should reset the Rateshaping and the bridge.                  |
#------------------------------------------------------------------------------

function restart {
	echo "restarting it all" 
	rateShapeOff
	bridgeDown
	sleep 1
	bridgeUp
	sleep 1
	. ./$RATEFILE

}

#------------------------------------------------------------------------------
# this displays the qdiscs classes and filters on each interface              |
#------------------------------------------------------------------------------

function rateShapeShow {
	echo ""
	echo $MODEM
	$TC qdisc show dev $MODEM
	$TC class show dev $MODEM
	$TC filter show dev $MODEM
	echo ""
	echo $INSIDE
	$TC qdisc show dev $INSIDE
	$TC class show dev $INSIDE
	$TC filter show dev $INSIDE
}

#------------------------------------------------------------------------------
# This function adds a new customer to the $RATEFILE file then reloads it     |
# and sets the counter up one more to prevent more than one device sharing a  |
# class and filter. It also restarts the rateshaping so the new entry is ran. |
#------------------------------------------------------------------------------

function addCust {
	let $COUNT+=1
	read -p "Enter the mac address of client you want to limit bandwidth to. eg A3:B3:C4:44:55:66 --> " MAC
	read -p "Enter their desired download speed in Kilobits per second eg 4096-->" DOWN
	read -p "Enter their desired upload speed in Kilobits per second 128-->" UP
	read -p "Enter and Name and any comments here-->" COMMENTS 
	echo " " >>$RATEFILE
	echo "#----------------------------------------------------------------">>$RATEFILE
	echo "#Name and Comments="$COMMENTS"">>$RATEFILE
	echo "#MAC Address="$MAC"">>$RATEFILE
	echo "#"$DOWN" kbps download speed">>$RATEFILE
	echo "${TC} class add dev $MODEM parent 1:0 classid 1:"$COUNT" cbq rate "$DOWN"KBit allot 1514 prio 1 avpkt 1000 bounded">>$RATEFILE
	echo "${TC} filter add dev "$MODEM" parent 1:0 protocol ip handle "$COUNT" fw flowid 1:"$COUNT"">>$RATEFILE
	echo "${EBTABLES} -A FORWARD -d "$MAC" -j mark --set-mark "$COUNT" --mark-target ACCEPT">>$RATEFILE
	echo "#"$UP"kbps upload speed">>$RATEFILE
	echo "${TC} class add dev inside parent 1:0 classid 1:"$COUNT" cbq rate "$UP"KBit allot 1514 prio 1 avpkt 1000 bounded">>$RATEFILE
	echo "${TC} filter add dev eth1 parent 1:0 protocol ip handle "$COUNT" fw flowid 1:"$COUNT"">>$RATEFILE
	echo "${EBTABLES} -A FORWARD -s "$MAC" -j mark --set-mark "$COUNT" --mark-target ACCEPT">>$RATEFILE
	echo 
	echo "COUNT="$COUNT>>$CONFIGFILE
	rateShapeRestart
}

#------------------------------------------------------------------------------
# This function deletes any file this script produces for a fresh start.      |
#------------------------------------------------------------------------------

function cleanUp {
	rm $RATEFILE
	rm $CONFIGFILE
}

#------------------------------------------------------------------------------
# This is the case structure that handles the menu selection it calls the     |
# it also refresh the config every time it is hit.                            |
#									      |
# For descriptions of functions look about the function                       |
#------------------------------------------------------------------------------

cd /usr/local/bridge
readConf
clear
menu
	while [ $X -lt 2 ]
		do
		readConf
		clear
		case "$CHOICE" in
		"1" )
			clear
			writeConfig
			menu
			
		;;

		"2" )
			clear 
			bridgeUp
			menu
			
		;;

		"3" )
			clear  
			bridgeDown
			menu
			
		;;

		"4" ) 
			clear	
			rateShapeOn	
			menu
			
		;;

		"5" )
			clear 
			rateshapeOff
			menu
			
		;;

		"6" )
			clear 
			rateShapeRestart
			menu
			
		;;

		"7" )
			clear 
			restart
			menu
			
		;;

		"8" )
			clear 
			rateShapeShow
			menu
			
		;;
 
		"9" )
			clear 
			addCust
			menu
			
		;;

		"10" )
			clear
			displayConf
			menu
			
		;;

		"11" )
			clear
			cleanUp
			menu
			
		;;
	
		"12" )
			exit
		;;

		* ) 
			echo "Please choose 1 -12. To exit press ctrl C"
			menu
		;;
	esac
done


#------------------------------------------------------------------------------
# ------------------------- Variable log --------------------------------------
#------------------------------------------------------------------------------
# int X is a counter and should never be changed by hand unless debuging       |
# string CONFIGFILE Where the ini file is saved                                |
# string RATEFILE is the location of the customer rateshapeing data            |
# string MODEM is the name for the "outer" network adpater                     |
# string INSIDE is the name for the "inner" network adapter                    |
# string BRNAME is the bridge name or ID used for brctl                        |
# int COUNTER is very important is is used to ID each user in the creation of  |
#	the classes filters and ebtables. This should only be changed by hand  |
#	when users are added to the RATEFILE by hand or some other script.     |
# string MAC is the users MAC address to be rate shaped                        |
# int UP is the upload rate that is desired measured in kiloBITs per second    |
# int DOWN is the download rate the is desired measured in kiloBits/s          |
# string COMMENTS is used as name and notes feild for each customer            |
#-------------------------------------------------------------------------------



```

I also would enjoy feedback if you find any bugs or other issues. (or easier ways):lolflag:

---

