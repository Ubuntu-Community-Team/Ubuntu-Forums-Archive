---
title: "Installion help for ePSXe?"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Logank9k on 2009-04-25
Okay, so I just finished setting up ePSXe with the plugins, bios, and other stuff by following a Linux how-to. Whenever I attempt to open it ( in the terminal ) I get the error message:

./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

I googled the problem, and some people said to look in /usr/lib32/ or /usr/lib64/ and copy libgtk-1.2.so.0 into the ePSXe folder. All I have is /usr/lib/ and it doesn't have a file called libgtk-1.2.so.0. If anyone could tell me where to download, or where to find libgtk-1.2.so.0 I'd be very grateful. :)

P.S.: I'm not using the program that can be found in Add/Remove, PCSX, because it randomly crashes sometimes.

---

### Post by Seks on 2009-04-25
run

```
sudo apt-get install libgtk1.2
```

---

### Post by Logank9k on 2009-04-25
> **Seks said:**
> run

```
sudo apt-get install libgtk1.2
```


Thank you very much! It works perfectly!

---

### Post by bikodog on 2009-04-29
I am having this exact same problem, but still getting the error after installing libgtk as mentioned above.

Any suggestions?

---

### Post by mkoehler on 2009-04-29
You might have to add the a link to the file in your lib directory: Try to find where it is located by typing in the following command:

```
sudo find /usr -iname "libgtk-1.2.so*"
```

---

