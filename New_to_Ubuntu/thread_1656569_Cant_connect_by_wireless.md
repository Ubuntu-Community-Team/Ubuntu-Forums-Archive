---
title: "Cant connect by wireless"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by TedinOz on 2010-12-31
I see this is a frequent problem for many and have read numerous threads and replies, none of which seem to have an answer for my situation.
I am using a SpeedTouchF0338C modem and can connect with the cable but wireless connection does not work even though the icon says it is connected. I am an absolute beginner here but from posts I have read I have pasted here the results of iwconfig  in the hope that someone can tell me what to do next.
Thanks

ted@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"SpeedTouchF0338C"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: B6:26:0E:E8:E3:BF   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by spiky001 on 2010-12-31
Hi iwconfig shows your wireless in adhoc mode is there a reason for that?

---

### Post by TedinOz on 2010-12-31
> **spiky001 said:**
> Hi iwconfig shows your wireless in adhoc mode is there a reason for that?

Hi thanks for looking at this. I'm sorry to say I have no idea why.. it's not something I have done, not consciously anyway but I guess you are telling me this is not right so any ideas on how to undo what's wrong and how to put it right will be greatly appreciated.

---

### Post by spiky001 on 2010-12-31
So you are trying to connect to the modem direct from pc? In network manager if you left click dose it show a list of networks, if so select your one (SpeedTouchF0338C) or what ever it is called,

---

### Post by TedinOz on 2010-12-31
> **spiky001 said:**
> So you are trying to connect to the modem direct from pc? In network manager if you left click dose it show a list of networks, if so select your one (SpeedTouchF0338C) or what ever it is called,


Please forgive my ignorance but where do I find network manager? What is happening here is when I log on,the wireless icon in the taskbar at top flashes and in a drop down shows the net work as available and I have selected that, keyed in the passkey etc and I get a notification that the wireless is connected and the icon stabilises  with ))) permanent signal. But when I try to access the internet I am told "Server not Found", "Check your internet Connection" Everything works fine when I connect the same modem by cable so whatever is wrong must be to do with the configurations somehow.

---

### Post by TedinOz on 2010-12-31
I am now happy to report that the problem is resolved and all is working well, thanks to this reply to an earlier post I made....

                                  **Re: Server not found/ Now partly resolved :)**             
                                                                     Quote:
                                                                      Originally Posted by **TedinOz**                                      
                 *...I connected the ethernet cable  from my wireless modem, got instant connection and internet access, so  it seems the earlier problem was with the Wireless connection which  although indicating full power, was not connecting to the server. ...*
                                 
                               
                                                                                                                                                                                                                                   #[**6**]("http://ubuntuforums.org/showpost.php?p=10300250&postcount=6")                                                                                  [TedinOz]("http://ubuntuforums.org/member.php?u=1214589")                      
                                                                                                        
             
                                                                                                   **Re: Server not found/ Now partly resolved :)**             
                                                                     Quote:
                                                                      Originally Posted by **QLee**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10300166#post10300166")                 
                 *What I would try in that situation  would be to disconnect the ethernet cable and right click the Network  Manager icon to Edit Connections, then go to the Wireless tab and delete  the connection, then add a new wireless connection and see if it works.  Not guaranteed but easy and quick to try.*
                                 
It is in my nature to to look for the hardest solution to the  easiest problem. You were so right and after a few clicks my problem is  solved! Thank you so much! This is a wonderful forum that matches the  spirit of Ubuntu and I am very happy to have proceeded with it! 

Thanks again!


The support system here is wonderful! Thank you all!

---

### Post by QLee on 2010-12-31
> **TedinOz said:**
> I am now happy to report that the problem is resolved and all is working well, thanks to this reply to an earlier post I made....

                                  **Re: Server not found/ Now partly resolved :)**             
                                                                     Quote:
                                                                      Originally Posted by **TedinOz**                                      
                 *...I connected the ethernet cable  from my wireless modem, got instant connection and internet access, so  it seems the earlier problem was with the Wireless connection which  although indicating full power, was not connecting to the server. ...*
                                 
                               
                                                                                                                                                                                                                                   #[**6**]("http://ubuntuforums.org/showpost.php?p=10300250&postcount=6")                                                                                  [TedinOz]("http://ubuntuforums.org/member.php?u=1214589")                      
                                                                                                        
             
                                                                                                   **Re: Server not found/ Now partly resolved :)**             
                                                                     Quote:
                                                                      Originally Posted by **QLee**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10300166#post10300166")                 
                 *What I would try in that situation  would be to disconnect the ethernet cable and right click the Network  Manager icon to Edit Connections, then go to the Wireless tab and delete  the connection, then add a new wireless connection and see if it works.  Not guaranteed but easy and quick to try.*
                                 
It is in my nature to to look for the hardest solution to the  easiest problem. You were so right and after a few clicks my problem is  solved! Thank you so much! This is a wonderful forum that matches the  spirit of Ubuntu and I am very happy to have proceeded with it! 

Thanks again!


The support system here is wonderful! Thank you all!


What? You posted another thread about the same problem? Don't let the moderators catch you doing that! :-)

---

