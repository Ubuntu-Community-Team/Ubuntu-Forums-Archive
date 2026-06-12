---
title: "Wireless connection fixed ubuntu"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by Extract_Here on 2009-12-19
[SIZE=4]I hate this problem the same thing happened to me when i first installed 9.04. Your going to need to achieve a direct connect from the router so you can get the correct software to install your wireless driver. 
 The things you will need to download 
1. ndiswrapper you can get this from the synaptic package manager 
(system>administrator>synaptic) 
2. You will need to find the driver for your wireless card(google search its brand name along with driver. eg. ("Belkin" Driver) download it even if its a Windows Exe. file 
3. Browse the windows exe. file and find the file with .inf on the end eg. (belkin.inf)
4. once you have found that file open up Ndiswrapper It has a different name in the menu its called windows wireless drivers. (system>admin>windows wireless drivers)
5. drag the .inf file into the NDiswrapper and your wireless should connect.

if your still having problems message me and we can talk further.


                                                                              [/SIZE]   [SIZE=4]                 __________________
                -May the Source be with you:KS[/SIZE]

---

### Post by coffeecat on 2009-12-19
Thank you for helping people with ndiswrapper but, because this post is in the Beginner's Section, it is going to mislead a lot of newcomers to Ubuntu.

The fact is that the majority of wireless chipsets work out of the box with the drivers that come with recent versions of Ubuntu. For some chipsets you need to connect with a wired connection to install firmware or drivers that can't be included for licensing reasons. And for a minority only, you need to use ndiswrapper in order to use the Windows driver. Ndiswrapper really ought to be a last resort option.

If anyone is having wireless problems, do not install ndiswrapper until you have thoroughly researched your particular problem. You need to know your wireless chipset and post your own help thread. There is a useful sticky in the [Networking and Wireless section]("http://Networking%20and%20Wireless%20section").

---

