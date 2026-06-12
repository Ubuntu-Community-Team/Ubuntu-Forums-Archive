---
title: "Cant connect WIFI (first time with Linux)"
date: 2018-04-22
forum: Networking &amp; Wireless
---

### Post by cirogg on 2018-04-22
Hi, its my first time with Ubuntu/linux. I just bought a new laptop. HP g6 250. It came with no O.S installed so i decided to intall Ubuntu.

I cant connect via WIFI. I dont know the problem. I tried doing some things reading on internet but anything worked.

I have the wireless-info.txt

Please help :(

---

### Post by jeremy31 on 2018-04-22
In terminal do ```
./wireless-info && cat wireless-info.txt | nc termbin.com 9999
```
Post the URL from the last line in terminal

---

### Post by cirogg on 2018-04-22
> **jeremy31 said:**
> In terminal do ```
./wireless-info && cat wireless-info.txt | nc termbin.com 9999
```
Post the URL from the last line in terminal

THanks for the answer. I did it and i got this. (Spanish, sorry)

cirogg@CiroGG-HP:~$ ./wireless-info && cat wireless-info.txt | nc termbin.com 9999
bash: ./wireless-info: No existe el archivo o el directorio


I just wrote what you said

---

### Post by cirogg on 2018-04-22
wireless-info wasnt a txt. Now i deleted the extension txt and tried doing the same.

I got Permission denied

---

### Post by jeremy31 on 2018-04-22
The issue is that your attachment in the first post was the script itself, not the results.  Do you have internet access to this laptop?

---

### Post by cirogg on 2018-04-22
> **jeremy31 said:**
> The issue is that your attachment in the first post was the script itself, not the results.  Do you have internet access to this laptop?

Yes, i am now with the Cable connection

---

### Post by jeremy31 on 2018-04-23
Try running the script again with cable connection

---

