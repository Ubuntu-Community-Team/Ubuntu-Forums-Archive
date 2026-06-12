---
title: "Problem with Adsl connection"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by necer_cheniki on 2010-03-03
Hello,
I tried to install an Adsl connection but without success, I added a new Adsl connection from the network manager applet with the username of my adsl  and the password  . After the configuration when I click to connection in the network connection applet , it seems loading or trying to establish the connection , but a pop up message appears and said **" wired network , you are disconnected"**. where is the problem , because I remember one day when I used Ubuntu for the first time( maybe Ubuntu 8. , the configuration of my adsl was very simple and without problems.

I tried to apply the following command to configure the PPPoE :
```
sudo pppoeconf

```and other command to connect to the internet , and it succeed , but it was very slow.

Now I am using the internet from a wireless network from another computer which  use Win7. If the problem solved ( I will able to use Adsl connection on Ubuntu) Can I create a wireless connection so that the other computer which use Win7 will be able to use it ?

---

### Post by necer_cheniki on 2010-03-04
Is there a solution to my problem ?

---

### Post by TBABill on 2010-03-05
I am trying to understand your problem. You said you are trying to connect to your ADSL, but then you mentioned a wireless router. I will answer based on the assumption you are trying to connect to the router that has security enabled (WEP/WPA?).
 
In Ubuntu Gnome there is an icon on the top panel for your wirless/wired connection. Right click on that icon to make sure wireless is enabled on your machine. Once that is done, left click on that same icon and choose the router you are trying to connect to (I have 4 come up when I do so because I see my neighbors' routers as well). When you do the Ubuntu should prompt you to enter your password if the system has security enabled (the router).  You should not have to take further steps unless the system is not recognizing your wireless adapter, which is another troubleshooting step if your wireless will not enable.
 
You can do a search for "wireless" or something similar along with the model of your wireless adapter (if you type lspci into a terminal it will tell you the name of the adapter if recognized).

---

### Post by necer_cheniki on 2010-03-06
thank you for the replay , I will explain my problem with other method :

I have two computers , the first laptop ,the second is a PC, and I have a dsl modem. My objective is establishing the connection in my Laptop witch use Ubuntu with my dsl modem , then share it with the other PC using wireless connection from the Laptop.

When I use win7 , I create  a PPPoE connection with username and password and connect it , then I create a wireless ad hoc connection to share the internet connection so the other computer (PC) can access to the internet using the wireless connection.

how can I do the same thing using Ubuntu ?

---

