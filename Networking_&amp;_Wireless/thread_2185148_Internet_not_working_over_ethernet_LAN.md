---
title: "Internet not working over ethernet LAN"
date: 2013-11-01
forum: Networking &amp; Wireless
---

### Post by dankojoffrey on 2013-11-01
Hi, my sister started using Ubuntu 13.10. Everything work fine, except she went to her University dormitory and she cannot connect to internet at all. 
They are using ethernet LAN (no wifi). In Windows  when she plugs in ethernet cable and she opens a web browser (chrome or firefox) some sort of dormitory login site loads and she can enter her username and password. 
But in Ubuntu nothing loads and internet doesn't work. I told her to check IP addresses and DNS. She said that in Windows they are completely different then in ubuntu.
So, I told her to write down the IP addresses from windows, and enter them manually into ubuntu. Then she entered the same address into web browser like Windows did. It worked. But After she restarted PC Internet stopped working again. So she had to boot into Windows and write down all the addresses again.

Do you have any idea what could be the cause...???

---

### Post by Kirboosy on 2013-11-01
It sounds like there is some sort of proxy that her Ubuntu machine isn't automaticall picking up. Did she have an IT person on campus setup her Windows for her? I would check her proxy settings for Firefox and Chrome on windows.

Also how is she entering the IP addresses? Once she changes the settings to "Manual" it should remember them after reboots.

Hope that helps!
~Caboose

---

### Post by dankojoffrey on 2013-11-01
Nobody setup her Windows connection. They just gave her usermane and password and it worked fine in Windows. There is no proxy setting in Windows. 

The thing is that Ubuntu sets IP addresses completely different then Windows. Different DNS, gate, IP, mask... everything is completle different. And when you use setting that Windows automatically setup, it works. So somehow Ubuntu is unable to find out correct settings that are required by the network. 


The ubuntu setting are remembered over reboot. Sometimes internet works even after reboot, but mostly not. I think that there is an IP address conflict, because I told her to change the last 3 digits of her IP and it worked (for a while). Now, after a week, it doesn't work anymore.


She also said that some of her friends had other Linux distros and they had to switch to Windows, because they didn't know how to get internet working.


Maybe some package is required in linux to identify correct network settings...??? Or somthing else...???

---

### Post by Kirboosy on 2013-11-01
Were there any "required" programs that she had to install on windows in order to gain internet access? (ie antivirus, custom school program, etc)


I'm trying to think of what could be so different between the two. 

I'm not sure how old her computer is but you could always setup a virtual machine of Ubuntu using [Virtualbox]("https://www.virtualbox.org/"). She would then be able to use Ubuntu within Windows. The internet for the Ubuntu Virtual Machine (VM) would piggy back off the Windows host. So all the connection problems shoud in theory be resolved. It would also prevent the need to reboot to switch OS.

---

### Post by dankojoffrey on 2013-11-01
No special software were installed in Windows. Just username + password - entered in campus website login. That's it.

Well running Ubuntu inside windows is no point for her. She was running windows until recently and she wanted to switch to Ubuntu. So I'm looking for a solution, in which she could stay only in Ubuntu.

---

### Post by Hadaka on 2013-11-01
Hi, in network mgr you can set up a second wired connection.
enter the data ..under MANUAL click and save. then when the
school network is used..simply chose wired network #2
see attached..
[ATTACH=CONFIG]247476[/ATTACH]

---

### Post by dankojoffrey on 2013-11-02
> **Hadaka said:**
> Hi, in network mgr you can set up a second wired connection.
enter the data ..under MANUAL click and save. then when the
school network is used..simply chose wired network #2
see attached..
[ATTACH=CONFIG]247476[/ATTACH]

ok, that's what she did as a workaround... but the there are a lot of students in my sisters campus and IP is dynamic, so there is usually an IP conflict, when she enters some random IP... it takes some time to guess the right number... and as soon as she turns off her PC her IP will be assigned to another user and she has to guess again... so I'm looking for a better solution then just guessing random IP...

---

### Post by sam51 on 2014-05-02
I have the same issue, but my internet in my dorm works with my own separate router. I have a google chromebook. The weird thing is that whenever i log in, in chrome, internet works over the school network but whenever I log into ubuntu, the school internet doesn't work... it only work with my own router... so is there any solution? I tired entering the IP address manually and it still doesn't work

---

