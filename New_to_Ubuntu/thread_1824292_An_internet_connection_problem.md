---
title: "An internet connection problem"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by abnordude on 2011-08-13
I dunno whether ubuntu is causing this problem, but sometimes.........no, make it most of the times, I lose my internet connection.

DETAILS

I have a BSNL Teracom modem with an unlimited net usage.
For quite many days before, I have this problem.
The DSL light of the modem keeps on blinking most of the time....
And when it appears to be stable, the Internet light becomes red in color.
At times, there will be a green light in the Internet. And then I can access the Internet.
But thats just for a minute or maybe 5.
I dunno what the problem is, but when I contacted the BSNL operators, they gave me another number to dial, who gave me another which was not working...
Ugh......I totally hate their service......


Please help me....

---

### Post by mmsmc on 2011-08-13
have you ever had this problem with a windows computer? it sounds to me like it is a hardware failure on the modem

---

### Post by abnordude on 2011-08-13
No. I've not had this problem while I was using windows....

But after I switched to Ubuntu, there still was no problem......

It was months later that I started to experience this problem, till then it was okay in Ubuntu..



One more thing....
I too think it maybe a hardware problem......
Maybe a modem problem.........
I'll have to check.

---

### Post by joncorp on 2011-08-13
check up the drivers of your machine, maybe ubuntu didn't installed the necessary internet drivers for your pc model, just check em on the drivers panel, i am sure that you have to download them in order to get them to work.

---

### Post by mmsmc on 2011-08-13
good point, but since he said it worked before in ubuntu, did u use 10.10 then upgrade to 11.04?

---

### Post by abnordude on 2011-08-13
Well....
I am able to access the Internet.
But only for
MIN -  a minute.
MAX - 5-10 minutes.

One day, it was hours....And after that, not connecting at all.....
Why is this happening?
I don't think it's the problem of the drivers....

I'm gonna give a last try at the BSNL center.......
Else I'm gonna go for other service providers......

---

### Post by lmarmisa on 2011-08-13
How is your computer connected to your modem?. Are you using an Ethernet cable or wireless?. 

Or is your modem connected by USB?.

---

### Post by elgordodude on 2011-08-13
You said it was working ok for months, did it start after a kernel update, or even a large update after putting updates off for a month or two? If so, this is a known problem, often solved by reinstalling drivers.

---

### Post by abnordude on 2011-08-13
> **elgordodude said:**
> You said it was working ok for months, did it start after a kernel update, or even a large update after putting updates off for a month or two? If so, this is a known problem, often solved by reinstalling drivers.


Could you explain please..

---

### Post by abnordude on 2011-08-13
> **lmarmisa said:**
> How is your computer connected to your modem?. Are you using an Ethernet cable or wireless?. 

Or is your modem connected by USB?.

I think it is connected by an Ethernet cable.

---

### Post by mmsmc on 2011-08-13
> **abnordude said:**
> Could you explain please..

did you go from 10.10 to 11.04? and, did you not update for a while, then do 1 large update?

---

### Post by lmarmisa on 2011-08-13
> **abnordude said:**
> I think it is connected by an Ethernet cable.

This detail is very important.

Your modem is an intelligent device that is involved in the management of the DSL protocols and in the transfer of IP frames between your LAN and the ISP data network. This equipment is autonomous. 

Ubuntu is unable to access to any DSL protocols or interfaces and therefore it can not disturb this DSL level of communications. Ubuntu send and receives IP packets using interfaces like Ethernet or Wifi (802.11). So, Ubuntu is not guilty.

I have found this link that could be useful for you:

 [http://www.corenetworkz.com/2010/06/setup-wireless-and-security-in-teracom.html](http://www.corenetworkz.com/2010/06/setup-wireless-and-security-in-teracom.html)


I recommend that you try to connect to your router in order to check if this device provides some kind of statistics about the quality of your DSL connection. Your problem seems related to the quality of connection of your telephone line. Maybe the quality changed by some reason (more noise, interferences with other lines) and your problems started.

---

### Post by elgordodude on 2011-08-13
> **abnordude said:**
> Could you explain please..

Well, if it is a Ubuntu problem, and not your ISP, (you don't seem super confident of this, and I can't blame you :) my ISP also sucks) then it follows that it is weird and thus significant that it was working for "months" and now doesn't. That leads to the question, what changed?

It appears that sometimes when the new kernel goes in the drivers lose their functionality, this is by far most common with proprietary video drivers, but it can happen with anything, sound, keyboards, even internet. There have been a lot of threads on this in the forums, but this one will sum most of them up:

[http://ubuntuforums.org/showthread.php?t=1656556](http://ubuntuforums.org/showthread.php?t=1656556)

So, did you update the kernel around the time it all started going screwy?

---

### Post by abnordude on 2011-08-13
> **mmsmc said:**
> did you go from 10.10 to 11.04? and, did you not update for a while, then do 1 large update?

Yes...That had happened once.

---

### Post by mmsmc on 2011-08-13
ok, then it might be your wireless drivers, but, i have just read your original post again, you are saying that your internet connection light on your modem changes colors right?

---

### Post by abnordude on 2011-08-13
Well, the DSL light keeps on blinking green....
And once it stops blinking, then the internet light becomes red in colour...
After that it stops and then DSL light again starts binking......

---

### Post by lmarmisa on 2011-08-14
The DSL light is a very poor information in order to diagnose the problem. Please, post the result of this command:

```

ifconfig

```

---

### Post by abnordude on 2011-08-14
> **lmarmisa said:**
> The DSL light is a very poor information in order to diagnose the problem. Please, post the result of this command:

```

ifconfig

```

The output is........


eth0      Link encap:Ethernet  HWaddr 70:71:bc:62:e6:3a  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7271:bcff:fe62:e63a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32963 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49515998 (49.5 MB)  TX bytes:2456252 (2.4 MB)
          Interrupt:20 Memory:fe400000-fe420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1680 (1.6 KB)  TX bytes:1680 (1.6 KB)

---

### Post by lmarmisa on 2011-08-14
> **abnordude said:**
> The output is........


eth0      Link encap:Ethernet  HWaddr 70:71:bc:62:e6:3a  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7271:bcff:fe62:e63a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32963 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49515998 (49.5 MB)  TX bytes:2456252 (2.4 MB)
          Interrupt:20 Memory:fe400000-fe420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1680 (1.6 KB)  TX bytes:1680 (1.6 KB)

Thanks. According to the command **ifconfig**, your private IP address is **192.168.1.2** and the private IP address of your modem is **192.168.1.1**.

I recommend to use the command **ping** for the diagnosis of your problem.

Open a first terminal and type the command:

```

ping -i2 192.168.1.1

```

The output will show the answers of your router to the ping requests. Do not abort this command or close the terminal.

Now open a second terminal and type this other command:

```

ping -i2 google.com

```

This second output will show the answers to the ping requests of a server on the internet. Do not interrupt this command or close the terminal until the end of the test.

Try to see both terminals simultaneously. 

And now this is the most important point of the test: check if, when the internet connection is stopped, the answers of your modem to the ping requests are not stopped.

I think that, during the periods of time that you have no access to internet (the DSL light is red), the flow of answers to ping coming from internet will stop but the answers coming from your modem will continue normally. If so, the problem will due to the DSL connection provided by your ISP and Ubuntu will be not guilty at all.

IMPORTANT: select a terminal and type [**Control-C**]("http://en.wikipedia.org/wiki/Control-C") if you want to abort the ping command.

I hope that this test will be useful for you.

Best regards,

Luis

---

### Post by dineshs on 2011-08-15
> The DSL light of the modem keeps on blinking most of the time....
It may a problem with telephone line/splitter.You may  ensure
that you do not have a parellel connection before splitter.
When your connection is OK open firefox type [COLOR="Blue"]192.168.1.1[/COLOR] in the address bar and hit enter.Type username and password as [COLOR="Blue"]admin[/COLOR].You will see the modem menu. note down the values of SNR,Attenuation and up/downstream speed (will be under device info-statistics-ADSL)
For a good line, SNR should be above 12
Attenuation should be below 40
Speed UP normally 512kbps and speed DOWN 2048.
Please let us know the values (SNR , attenuation and the UP/DOWN speeds).Also is the situation improved when you connect modem directly to the line (no splitter and phone on line)?
What is the distance between your modem and the telephone exchange?

---

### Post by abnordude on 2011-08-15
> **dineshs said:**
> It may a problem with telephone line/splitter.You may  ensure
that you do not have a parellel connection before splitter.
When your connection is OK open firefox type [COLOR=Blue]192.168.1.1[/COLOR] in the address bar and hit enter.Type username and password as [COLOR=Blue]admin[/COLOR].You will see the modem menu. note down the values of SNR,Attenuation and up/downstream speed (will be under device info-statistics-ADSL)
For a good line, SNR should be above 12
Attenuation should be below 40
Speed UP normally 512kbps and speed DOWN 2048.
Please let us know the values (SNR , attenuation and the UP/DOWN speeds).Also is the situation improved when you connect modem directly to the line (no splitter and phone on line)?
What is the distance between your modem and the telephone exchange?

No, it happens when the modem is directly connected to the line.

And about the details...........



Internet Connection               		                                                      	                                                                  	                    	 	                      DSL Status 	                                                Connected                            	           	           	           	                                       	                  Downstream Data Rate                           7684 Kbps                             	           	                                       	                  Upstream Data Rate                           816 Kbps                             	                                                                                    Downstream Attainable Data Rate                           8359 Kbps                                                                                                                         Upstream Attainable Data Rate                           1323 Kbps                                                 	          	                                                                                    	                  SNR (Downstream)                           6.80 dB                                            	                	  		          	                                             	                  SNR (Upstream)                           12.5 dB                                 	                 	              		       	     	                                     	                  Line Attentuation(Downstream)                           14.5 dB                                  	                  	                                             	                  Line Attentuation(Upstream)                           7.5 dB                                  	             		      			       	          	                        	                        	                        	                        	                        	                        	   	   		                         	        Gateway                 automatically set                  	   	  	    		                         	        Primary DNS 		  		                 218.248.255.141 				                  	   	  	   			   		 		                         	        Secondary DNS                 218.248.245.1

---

### Post by dineshs on 2011-08-15
> Internet Connection DSL Status Connected Downstream Data Rate 7684 Kbps Upstream Data Rate 816 Kbps Downstream Attainable Data Rate 8359 Kbps Upstream Attainable Data Rate 1323 Kbps SNR (Downstream) 6.80 dB SNR (Upstream) 12.5 dB Line Attentuation(Downstream) 14.5 dB Line Attentuation(Upstream) 7.5 dB Gateway automatically set Primary DNS 218.248.255.141 Secondary DNS 218.248.245.1
From the given data I think it is a problem with the port setting done at BSNL end,The result shows a higher speed of 8 Mbps being set on your line.If you do not have an IPTV connection you need only say 2Mbps (assuming your unlimited broadband plan is of speed less than 2Mbps).So I suggest you ask BSNL customer care to reduce the line profile to 2Mbps or less.BTW What unlimited plan are you using?UL750?

---

### Post by abnordude on 2011-08-19
> **dineshs said:**
> From the given data I think it is a problem with the port setting done at BSNL end,The result shows a higher speed of 8 Mbps being set on your line.If you do not have an IPTV connection you need only say 2Mbps (assuming your unlimited broadband plan is of speed less than 2Mbps).So I suggest you ask BSNL customer care to reduce the line profile to 2Mbps or less.BTW What unlimited plan are you using?UL750?

I'm using UL625

---

### Post by dineshs on 2011-08-19
> **abnordude said:**
> I'm using UL625
So the speed of the plan is only 256kbps and the port setting is for 8Mbps.If the port is set for a high speed it will not support long distance.(If the cable is good 2Mbps will work for 5km,8Mbps for 2Km and 24Mbps for just 1km-This is what I understand).Any way please ask them to reduce the port setting to 2Mbps or less.

---

### Post by abnordude on 2011-08-19
> **dineshs said:**
> So the speed of the plan is only 256kbps and the port setting is for 8Mbps.If the port is set for a high speed it will not support long distance.(If the cable is good 2Mbps will work for 5km,8Mbps for 2Km and 24Mbps for just 1km-This is what I understand).Any way please ask them to reduce the port setting to 2Mbps or less.

Is there any way to reduce the port settings manually.
I called BSNL and they just seem to be giving me phone numbers to other BSNL centers.

---

### Post by dineshs on 2011-08-19
> Is there any way to reduce the port settings manuallyYour modem only displays the value set by BSNL so the only way is to request them change the port setting.I have sent you a private message.Pl check.

---

### Post by abnordude on 2011-08-20
Yes. I have replied to that private message.

---

### Post by abnordude on 2011-08-26
Yes. I was able to fix this problem.
Thanks everyone for helping.
Especially dinesh.

---

