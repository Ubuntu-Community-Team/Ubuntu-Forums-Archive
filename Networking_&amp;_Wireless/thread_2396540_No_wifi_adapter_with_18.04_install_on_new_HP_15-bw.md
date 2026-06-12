---
title: "No wifi adapter with 18.04 install on new HP 15-bw040ng"
date: 2018-07-17
forum: Networking &amp; Wireless
---

### Post by jimberlin on 2018-07-17
I'm a complete novice with Linux. I just booted my new computer to 18.04 using a USB flash drive. It's up and running but no WiFi adapter available. Can someone help me? If you provide code to solve this problem then I'll need to know how to insert the code (never done it before). If you need to see a report from the computer I will need to know how to do that too.

Thanks for your help!

---

### Post by wildmanne39 on 2018-07-17
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created. d

---

### Post by slickymaster on 2018-07-17
Thread moved to **Networking & Wireless** for a better fit

---

### Post by chili555 on 2018-07-17
> **jimberlin said:**
> I'm a complete novice with Linux. I just booted my new computer to 18.04 using a USB flash drive. It's up and running but no WiFi adapter available. Can someone help me? If you provide code to solve this problem then I'll need to know how to insert the code (never done it before). If you need to see a report from the computer I will need to know how to do that too.

Thanks for your help!You can open a terminal in which to run the code, in this case, the wireless script, with the keyboard combination Crtl+Alt+t  (t for terminal!).

Once we see the result we'll propose a very detailed answer.

---

### Post by jimberlin on 2018-07-17
I attempted running the "Wireless Script" from Wildmanne39 and this is what came up on my terminal. The result was:  

[Inserted Code]
E: The update command takes no arguments

[Inserted Code]
E: Unable to locate package pastebinit

[Inserted Code]
Resolving github.com (github.com)... failed: Name or service not known.
wget: unable to resolve host address 'github.com'


Maybe I'm not doing what your asking. Here are also 2 screenshots of what I have or don't have.

---

### Post by jimberlin on 2018-07-17
I couldn't download the screenshots

---

### Post by wildmanne39 on 2018-07-17
It looks like you did not just copy and paste the the commands and there fore may have added another character that caused that error, could you please post the exact way that you ran the commands?

You can use the attachment facility by clicking on the paperclip or use url's for posting images.

Are you the person that emailed the output to me from the script?

---

### Post by chili555 on 2018-07-17
> **jimberlin said:**
> I attempted running the "Wireless Script" from Wildmanne39 and this is what came up on my terminal. The result was:  

[Inserted Code]
E: The update command takes no arguments

[Inserted Code]
E: Unable to locate package pastebinit

[Inserted Code]
Resolving github.com (github.com)... failed: Name or service not known.
wget: unable to resolve host address 'github.com'


Maybe I'm not doing what your asking. Here are also 2 screenshots of what I have or don't have.Did you have an internet connection at the time? It is required.

---

### Post by jimberlin on 2018-07-17
I'm writing to you from a different computer so I can't understand how I would be able to copy and paste since the new computer is not online and can't receive your code. If I sent you something I don't know how it happened. Sorry for such confusion. I have never worked with Linux before.

---

### Post by jimberlin on 2018-07-17
I will type the code into the text editor on the new computer and then copy and paste it to the terminal.

---

### Post by jimberlin on 2018-07-17
I am completely lost on all of this. I think I need to find someone locally to work on this for me. Thanks for your help.

---

### Post by wildmanne39 on 2018-07-17
It is up to you but if you do not have a wired internet connection you can tether your cell phone to your computer with 18.04 booted using the flash drive and that will create a internet connection for you.

---

### Post by chili555 on 2018-07-17
> **jimberlin said:**
> I am completely lost on all of this. I think I need to find someone locally to work on this for me. Thanks for your help.Let's take a few simple steps and see if we can work this out. Please open a terminal as I described above and run:```
lspci -nnk | grep 0280
```That funny pipe symbol | is on the right side of my US keyboard on the same key with \.

Copy the result and use some other computer to post it here.

We can do this.

---

