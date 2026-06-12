---
title: "WiFi not working in Thinkpad E470"
date: 2017-10-18
forum: Networking &amp; Wireless
---

### Post by julian102 on 2017-10-18
Hi, sorry to use your thread as well, but I got the same problem with my new Thinkpad E470.
Connected via cable my internet works just fine, but I'm not able to get a WIFI signal or anything like that.

Unfortunately I'm completley new into Ubuntu 16.04 LTS, normally using Windows. 
I tried to run your wireless info script as well, but it didn't create such an info text. I tried to start it as a program.
I guess I did a misstake, but don't know which. Hopefully you can give me a short hint how to do it.

Hopefully you might help me as well. 
Thanks a lot for your time.

---

### Post by slickymaster on 2017-10-18
Moved to a thread of its own.

Please open a terminal window (Ctrl+Alt+T), copy/paste and run the following commands```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

---

### Post by julian102 on 2017-10-18
Hi slickymaster,

first of all thanks a lot for your fast help, I really appreciate it.
In the link below I copied the results of the wireless-info.txt

[https://pastebin.com/FxNVZpw4](https://pastebin.com/FxNVZpw4)

Hopefully you can help me.

---

### Post by jeremy31 on 2017-10-18
I don't think that chipset is supported yet in Linux

---

### Post by julian102 on 2017-10-19
Hi, 
thanks for your help. 
Is there special way how I can check if the chipset is supported or not? Because in the meantime I would use Win10, but would like to switch to Ubuntu as fast as possible.

---

### Post by julian102 on 2017-10-25
Can anyone tell me how and where I'm able to check whether my chipset is supported yet or not.
Thanks for your help.

---

### Post by kurt18947 on 2017-10-25
WiFi chipset support is probably the biggest hardware difficulty using Ubuntu. New wifi chipsets are released every few months and some manufacturers make linux support a very low priority. The simplest solution especially for someone new to the Ubuntu/Linux way of doing things is to get a USB wifi adapter that is known to work out of the box. If you get the right one, just plug it in, enter the network details and you're in business. Get the wrong one and you're in for a period of frustration. 

I used to be fairly familiar with preferred wifi adapters but haven't needed to mess with them in a couple years. Most Intel WiFi adapters work well if your system supports them. Some notebooks have whitelisted wifi adapters and those are the only ones that will work without modding the BIOS. A USB wifi adapter, perhaps a low profile one that only sticks out about 10 mm is the simplest until your integral chipset is supported. Plus, I've found it useful in the past to have a USB wifi adapter that I KNOW will connect without messing about even if I don't need it for day to day use.

---

### Post by kurt18947 on 2017-10-29
> **julian102 said:**
> Can anyone tell me how and where I'm able to check whether my chipset is supported yet or not.
Thanks for your help.

Sorry you haven't gotten a reply to your question. One pretty good source IME is wikidevi.com. I don't know how up-to-date their info is.

---

### Post by praseodym on 2017-10-29
Pastebin output is not available anymore. Please post it again

---

### Post by jeremy31 on 2017-10-29
I think it was the rtl8821ce and the driver might show up at [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new) or [https://github.com/lwfinger/](https://github.com/lwfinger/)

---

### Post by praseodym on 2017-10-29
[https://ubuntuforums.org/showthread.php?t=2371149&page=3&p=13702710#post13702710](https://ubuntuforums.org/showthread.php?t=2371149&page=3&p=13702710#post13702710)

Try this one

---

### Post by kurt18947 on 2017-10-30
> **praseodym said:**
> [https://ubuntuforums.org/showthread.php?t=2371149&page=3&p=13702710#post13702710](https://ubuntuforums.org/showthread.php?t=2371149&page=3&p=13702710#post13702710)

Try this one

Would that solution work on 16.04 with kernel 4.4?

 		                                                                                                                                                    5 Days Ago                                                                                                                                                                                                     [#23]("https://ubuntuforums.org/showthread.php?t=2371149&p=13702710#post13702710")                                                                                                                                                                                      		
  		 			 				 				 					 						 	[**[COLOR=#000000]evassilyev[/COLOR]**]("https://ubuntuforums.org/member.php?u=2080869") 	 
 						[IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]  					 					 						First Cup of Ubuntu 					 					 						[IMG]https://ubuntuforums.org/images/rank_1.png[/IMG] 					                                           					 					 						 							     						
 					 				
 			
 			 				 					Join DateOct 2017
Beans1
 					 					 				
 			 		
 	
  	 		 		 		 		[h=2][SIZE=3]Re: Unable to activate wireless on ThinkPAD E570 with Loki 0.4.1 		[/SIZE][/h] 		 				 				 					 				 		 			 				 					[B][COLOR=#242729][FONT=Arial]Worked solution[SIZE=6] [SIZE=5](Requirements: kernel >=4.11) :
[/SIZE][/SIZE][/FONT][/COLOR][/B][COLOR=#242729][FONT=Arial]
Be worth a try on 17.10 though.[/FONT][/COLOR]

---

### Post by ajesteves on 2018-04-17
This solution worked for me, you must first upgrade to kernel 4.15. 

[https://ubuntuforums.org/showthread.php?t=2371149&page=3&p=13702710#post13702710](https://ubuntuforums.org/showthread.php?t=2371149&page=3&p=13702710#post13702710)

---

