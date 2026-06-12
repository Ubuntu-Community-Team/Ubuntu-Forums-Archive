---
title: "Wireless Networking"
date: 2014-01-01
forum: Networking &amp; Wireless
---

### Post by benmcneil102 on 2014-01-01
I have a dual boot machine and have noticed that my Ubuntu 12.04 boot is getting slow internet, although my windows 8 is getting regular full speed.  I was curious to know if there are any solutions I can try.   Is it simply better to switch to a more linux friendly wireless adapter or something else I could try.

I currently have this wireless card 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833166073](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166073)

I am open to try anything I was thinking of getting this since TP-Link is more linux friendly


[http://www.amazon.com/gp/product/B002T4D3M2/ref=s9_simh_gw_p147_d0_i2?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=1DP3V1Z9SDD14KEZY30Y&pf_rd_t=101&pf_rd_p=1688200382&pf_rd_i=507846](http://www.amazon.com/gp/product/B002T4D3M2/ref=s9_simh_gw_p147_d0_i2?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=1DP3V1Z9SDD14KEZY30Y&pf_rd_t=101&pf_rd_p=1688200382&pf_rd_i=507846)

Thanks in advance

---

### Post by benmcneil102 on 2014-01-01
I found that there is a driver how do I install it or check that I have it  [http://www.rosewill.com/products/1870/ProductDetail_Download.htm](http://www.rosewill.com/products/1870/ProductDetail_Download.htm)

---

### Post by wildmanne39 on 2014-01-01
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by benmcneil102 on 2014-01-01
Ok here you go

---

### Post by benmcneil102 on 2014-01-02
Would this work for me?

[http://ubuntuforums.org/showthread.php?t=1927750](http://ubuntuforums.org/showthread.php?t=1927750)

---

### Post by wildmanne39 on 2014-01-03
No I doubt it would work because that driver is for 10.04 and most likely if it is still available at that link it will probably not compile.  Please try what is at this link.
[http://ubuntuforums.org/showthread.php?t=2039809](http://ubuntuforums.org/showthread.php?t=2039809) post 6.

Here are the screenshots mentioned in that link.
Thanks

---

### Post by benmcneil102 on 2014-01-31
I'm still having the same problem connection is good for a few minutes but then drops to basically nothing

---

