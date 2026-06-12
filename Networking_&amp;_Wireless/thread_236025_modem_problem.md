---
title: "modem problem"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by maalvin15 on 2006-08-14
to all GURUS,

please help me im a newbie in linux and i have a big problem on my modem. i cant install my modem, it is dfm-562is, can you guide me in installing my modem... please help me coz im starting to love linux and hating windows ehehe... thnx for your time and reply....

---

### Post by drtvasudevan on 2006-08-14
> **maalvin15 said:**
> to all GURUS,

please help me im a newbie in linux and i have a big problem on my modem. i cant install my modem, it is dfm-562is, can you guide me in installing my modem... please help me coz im starting to love linux and hating windows ehehe... thnx for your time and reply....

* To configure dialup

```
sudo pppconfig
```

* To connect dialup

```
sudo pon provider_name
```

* To disconnect dialup

```
sudo poff
```

---

### Post by maalvin15 on 2006-08-14
thnx for the reply.. just 1 question.. where can I get a driver for dfm-562is hsfi modem? i am using dapper drake... thanx for the reply.

---

### Post by blent07 on 2006-08-14
Hey, I'm new to Linux myself, but I do know something about my own modem issues. If your modem is internal, it could very well be a "Winmodem," which is actually more of a chipset on the motherboard with a specific driver that allows Windows to use it. Getting a driver for them is difficult and people are working to improve it. You have to download a program to run in Ubuntu to get some data on the modem, then send that in for someone to find a driver for you.

Check here:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
Or try here:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_identify_Modem_chipset](http://easylinux.info/wiki/Ubuntu_dapper#How_to_identify_Modem_chipset)

 At least, that's the solution I found. I haven't done that yet, but I'm using an external modem instead.

Setting up an external is easier. In configuring your connection, just use Autodetect or point it to the number one less than the serial port it's using. Assuming it uses a serial port that is... For example, my Dell only has one serial port, so I point the connect to look at ttyS0 for my modem. I'm having some troubles myself, though, and I'm looking into them. Hope that provides some help. 

Again, I'm real new in this, so take everything I said with one massive grain of salt.

---

### Post by zxee on 2006-08-14
Sometimes the 1st place to start (with winmodems or if you're unsure whether or not your modem is a softmodem) is here: [http://www.linmodems.org/](http://www.linmodems.org/)
You can then download the scanmodem tool. Look for it under the section titled "Status". After running scanmodem you should know if your modem is supported in linux or not. 
For setting up a supported modem see the link in my sig.

---

