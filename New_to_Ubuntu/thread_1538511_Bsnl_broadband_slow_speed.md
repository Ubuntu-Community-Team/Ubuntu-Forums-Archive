---
title: "Bsnl broadband slow speed"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by anand_30 on 2010-07-25
I am using ubuntu 10.04 64bit,dual boot windows 7 with BSNL broadband 500c plan.

Recently i am experiencing very slow speed on browsing and downloading.Most websites even don't open such as facebook,ubuntuforums.The only website seems to open is google.

But in windows 7 speed is ok,it is less as compared to usual speed but it is definitely better than speed in ubuntu.And most of the websits open.

I have set my broadband as follows:-
Network connections>DSL>New
In that i have entered username and password and set ip as automatic.Previously this was doing really well and was giving more speed as compared to windows.

But now its very awful.Am i doing wrong in setting my connection(I don't like the conventional way of using pppoeconf as it causes disappearance of network symbol.)

The only thing I have done recently is that i have add an addon-Adblock Plus,but i don't think that is causing any problem.

Any ideas???Or I should wait for few more days as my ISP bsnl has its own reputation in providing slow speeds and sever down problems...;) or i should enter ips manually but i don't know them.:(

Thanks in advance.:)

---

### Post by wojox on 2010-07-25
Try disabling [IPv6]("http://wojox.homelinux.org/?p=46")

---

### Post by dineshs on 2010-07-25
Are you using DSL connection via Network manager to connect?MTU may also cause problems.
What is the model name of your modem?

---

### Post by anand_30 on 2010-07-25
> **wojox said:**
> Try disabling [IPv6]("http://wojox.homelinux.org/?p=46")
Just tried that but no luck.
But thanks for your advice.:D

---

### Post by anand_30 on 2010-07-25
> **dineshs said:**
> Are you using DSL connection via Network manager to connect?
Yes.

> **dineshs said:**
> 
MTU may also cause problems.
What is the model name of your modem?

My modem is Huawei SmartAX MT882 ADSL Router.Its very ancient i think..:lol:

---

### Post by dineshs on 2010-07-25
My advice is to configure this modem in PPPoE mode ,so that you no longer require a PPPoE dialler in windows or DSL connection in ubuntu to connect / disconnect.Pl try this site to configure modem in PPPoE (always ON mode)If your configurations are correct ,the ADSL-link lamp will become orange and stable)
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html) 
click modem/CPE configuration

---

### Post by anand_30 on 2010-07-25
> **dineshs said:**
> My advice is to configure this modem in PPPoE mode ,so that you no longer require a PPPoE dialler in windows or DSL connection in ubuntu to connect / disconnect.Pl try this site to configure modem in PPPoE (always ON mode)If your configurations are correct ,the ADSL-link lamp will become orange and stable)
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html) 
click modem/CPE configuration
I struck at first step only,its open ***192.168.1.1 ***in browser which i cant open,its saying problem loading page.Sorry i am still new to this type of modem configuration.

---

### Post by dineshs on 2010-07-25
that modem is not DHCP enabled by default.Please set IP manually as follows Then try

Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you want and click edit(you can add the ethernet connection if not listed) 
select ipv4 
method-manual 
click add 
address 192.168.1.100 
mask 255.255.255.0 
gateway 192.168.1.1 
[COLOR="Red"]then hit enter [/COLOR]
DNS 4.2.2.1
then click apply

---

### Post by Fifthmarch on 2010-07-25
Check when your speed dropped. Was it after you changed any of your hardware/software settings? As a BSNL user, I know that the fault is probably at their end.

---

### Post by anand_30 on 2010-07-25
> **dineshs said:**
> that modem is not DHCP enabled by default.Please set IP manually as follows Then try

Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you want and click edit(you can add the ethernet connection if not listed) 
select ipv4 
method-manual 
click add 
address 192.168.1.100 
mask 255.255.255.0 
gateway 192.168.1.1 
[COLOR=Red]then hit enter [/COLOR]
DNS 4.2.2.1
then click apply
Worked like a charm.Thank you so much.I have seen most of your replies as solutions in this forums for questions related to broadband and modem configuration.I appreciate your help.You are great.Thank you soooooo much.

I know this is not a place to ask but how to set connection in this type in windows 7?

---

### Post by dineshs on 2010-07-25
Open network and sharing centre via control panel.click manage network connections-right click on local area connection-click properties-double click on ipv4
IP address [COLOR="Blue"]192.168.1.100[/COLOR]
mask [COLOR="Blue"]255.255.255.0[/COLOR]
gateway [COLOR="Blue"]192.168.1.1[/COLOR]
primary DNS [COLOR="Blue"]192.168.1.1[/COLOR]
secondary DNS not required
apply
Now use your web browser directly
(You can also use BSNL DNSs or open DNS like 4.2.2.1 or 8.8.8.8 )
Happy to hear your problem is solved.Enjoy ubuntu

---

### Post by anand_30 on 2010-07-26
> **dineshs said:**
> Open network and sharing centre via control panel.click manage network connections-right click on local area connection-click properties-double click on ipv4
IP address [COLOR=Blue]192.168.1.100[/COLOR]
mask [COLOR=Blue]255.255.255.0[/COLOR]
gateway [COLOR=Blue]192.168.1.1[/COLOR]
primary DNS [COLOR=Blue]192.168.1.1[/COLOR]
secondary DNS not required
apply
Now use your web browser directly
(You can also use BSNL DNSs or open DNS like 4.2.2.1 or 8.8.8.8 )
Happy to hear your problem is solved.Enjoy ubuntu
Thank you very much.Bsnl now working perfectly on ubuntu as well as window.

Again thanks Dineshs for your help.:D

---

### Post by dineshs on 2010-07-26
Good.Thank you.

---

### Post by ravikandagal1 on 2013-01-02
Hi ,

I am using Ubuntu 12.4 and using the BSNL broadband . I have the BSNL modem AR800v model modem . I am also facing the same issue of slow speed compared to windows.

I have configured the Network connections as "Wired" . The broadband connections works , but it is slow compared to Windows. Please help me.

---

