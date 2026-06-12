---
title: "extra restricted and nvidia 6150"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by absbegstarting on 2009-02-01
Hellooo!!! More than all I wanna thank you especially to i guess it was Aysiu who published that post in which recommended the tutorial of psychocats, which I used to install Ubuntu after a loong time I wanted to do that...
Then I found just 2 problems that I cannot solve just there, probably something I didnt do right:oops::oops:
Point 1: I cant download the restricted extras ubuntu, it just tells me "aplications list not available" and that I need to reload, that I need the  Internet...gives me 2 butons: refresh or close, I press refresh and go the start of this again...its a circle (if I close nothing happens)
Point 2: when trying to install nvidia drivers, for my 6150 onboard (asus m2n-mx se plus am2+) it appears a window that gives me a choice between 173 and 177 versions, whatever I choose it says it is not available, clik on "habilitar" (make it available, dont know the verb in english:() and it seems to be installing something but then comes back to the same dialogue...so I dont know what to do...please HELP!!!

---

### Post by absbegstarting on 2009-02-01
Hello, I need an answer please...say me that I did everything wrong at least , but I want to know what is it about please:confused:
...or you just tell me [-X
:D

---

### Post by absbegstarting on 2009-02-01
I put this screenshots that may help you helping me...:D

---

### Post by cariboo on 2009-02-01
It sounds like the server you are trying to update and download from has a problem. Go to Sytem-->Administration-->Software Sources, from the download from dropdown select Main. It will then ask you to update your sources list. Once the list is updated, you can use Applications-->Add/Remove Programs or System-->Administration-->Synaptic Package Manager to install the packages you need.

Jim

---

### Post by absbegstarting on 2009-02-01
Thank you, Iwas trying to use Uruguay server, or i dont know the word...Ill try what you say and tell you how does it work !! Thank you!

---

### Post by absbegstarting on 2009-02-01
Yes there is a problem there but I dont know what it is about, cause Ive selectec all the options in the dialogue window, and in the server Uruguay, and now Ive found for the second time every source deselected, and main server by default...it is like it doesnt save the changes...??what is this about??

---

### Post by unutbu on 2009-02-01
Please open a terminal (Applications>Accessories>Terminal)
and type:
```

cat /etc/apt/sources.list
sudo apt-get update
```

Please show us the output.

---

### Post by absbegstarting on 2009-02-01
Yes, really thank you but Ive done that before, because it said the tutorial so. But, do you know what, I discovered now two things: that I had reciently installed the OS and asked for 248 updates (yes, 248), and that now somehow it didnt automatically deselect all the options that I said in last post, there probably was something I was doing wrong...now Im just updating with everything the OS found that says it needed...then Ill try with the extras and the driver, probably tomorrow, and Ill tell you...a big big thank you!!:popcorn:

---

### Post by absbegstarting on 2009-02-01
No,no...I looked and I havent done that, but something similar, some kind of backup (that I dont even know where is it:p)..but the question is : can I do that comand while "update manager" is working with so much updates...or better I wait until it finishes with it all??

---

### Post by unutbu on 2009-02-01
I think (you are right) only one apt program should run at a time.
So let Update Manager finish. If Update Manager is working, then there may be no need to run the commands I suggested above.

---

### Post by absbegstarting on 2009-02-01
> **unutbu said:**
> I think (you are right) only one apt program should run at a time.
So let Update Manager finish. If Update Manager is working, then there may be no need to run the commands I suggested above.
Yes, it seems it was a problem of updates like you said before,** thank you** very much, and of course later Ill tell you later if everything goes fine

---

