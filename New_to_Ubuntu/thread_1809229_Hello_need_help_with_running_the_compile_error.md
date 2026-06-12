---
title: "Hello need help with running the compile error"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by avi k on 2011-07-21
[SIZE=3]I installed the software wrf and the wps, now I'm trying to install a package called ARWpost, instructor page here:

 [http://www.mmm.ucar.edu/wrf/OnLineTutorial/Graphics/ARWpost/compile.htm](http://www.mmm.ucar.edu/wrf/OnLineTutorial/Graphics/ARWpost/compile.htm)

 Now when I do the compile command, I get an error: Here is the[/SIZE][SIZE=3] compile[/SIZE][SIZE=3]  log :

[/SIZE][http://pastebin.com/UQu769m9](http://pastebin.com/UQu769m9)

[SIZE=3]If anybody has any idea what the error says I'd like help[/SIZE].
[SIZE=3]
[/SIZE][SIZE=3]Thanks

Avi .[/SIZE]

---

### Post by ankspo71 on 2011-07-21
Hi,
Here are some more detailed instructions to compile arwpost.
[http://www.mmm.ucar.edu/wrf/users/graphics/ARWpost/ARWpost.htm](http://www.mmm.ucar.edu/wrf/users/graphics/ARWpost/ARWpost.htm)
(it includes a download link for different versions)

The error message is an "exit status 1", and according to a Man page for Make.....
> 
EXIT STATUS
GNU make exits with a status of zero if all makefiles were successfully parsed and no targets that were built failed.  A status of one will be returned if  the  -q  flag  was used and make determines that a target needs to be rebuilt. A status of two will be returned if any errors were encountered.
[http://unixhelp.ed.ac.uk/CGI/man-cgi?make](http://unixhelp.ed.ac.uk/CGI/man-cgi?make)


---

### Post by avi k on 2011-07-21
[SIZE=3]Thank you.

 But I do not understand, it says in the link you gave me, I need to install the wrfv2, so I can install the arwpost, if I install this version it does not spoil the version already installed on my computer wrfv3.2?.

[/SIZE]

---

### Post by MG&amp;TL on 2011-07-21
Your english is not at all bad. :)

However, I believe that there is Spanish ubuntu support available-see here:

[http://www.ubuntu.com/support/community/locallanguage](http://www.ubuntu.com/support/community/locallanguage) 

If you feel more comfortable speaking in your native language. If you already knew about this, then apologies. I do sympathise, I used a French forum for a week, and it was a nightmare. I do speak French, but conversational French, not IT-support french. :(

---

### Post by Wim Sturkenboom on 2011-07-21
The error starts on line 137 and the next lines (undefined reference to ...) basically state that you're missing a library (or that a file is not compiled, but that is in this case less likely) that contains the functions.

The missing functions are in the library of the newer version (I guess), hence the advise that was given.

That's all that I can say.

---

### Post by ankspo71 on 2011-07-21
Hi,
I think wrfv3 will be okay so I don't think you will need to download wrfv2. The page says the page was last updated in 2008, so I think the page needs updating to include instructions for wrfv3. 

According to the instructions, it says to open the "configure.arwp" file and make sure the path is correct to WRFV.

> Wim Sturkenboom said:
The missing functions are in the library of the newer version (I guess), hence the advise that was given.

I only mentioned the different versions because I can sometimes get around compile errors by trying to compile different versions of various software.

---

### Post by avi k on 2011-07-22
> **ankspo71 said:**
> Hi,
I think wrfv3 will be okay so I don't think you will need to download wrfv2. The page says the page was last updated in 2008, so I think the page needs updating to include instructions for wrfv3. 

According to the instructions, it says to open the "configure.arwp" file and make sure the path is correct to WRFV.



I only mentioned the different versions because I can sometimes get around compile errors by trying to compile different versions of various software.




 in  the configure.arwp file ,There is no path : Here is the configure.arwp file :


[http://pastebin.com/aG4pWRsb](http://pastebin.com/aG4pWRsb)

---

### Post by avi k on 2011-07-22
> **MG&TL said:**
> Your english is not at all bad. :)

However, I believe that there is Spanish ubuntu support available-see here:

[http://www.ubuntu.com/support/community/locallanguage](http://www.ubuntu.com/support/community/locallanguage) 

If you feel more comfortable speaking in your native language. If you already knew about this, then apologies. I do sympathise, I used a French forum for a week, and it was a nightmare. I do speak French, but conversational French, not IT-support french. :(



Thanks for the compliments.
 But I need support in Hebrew, the problem is that in Israel there are not many people know about the software wrf, and especially in the Ubuntu forum.
 And you're absolutely right, my English is not great.

---

### Post by kenimor on 2011-11-15
Can someone please help me with the problem I am having compiling the WRF on my computer. After successful configuration, I tried compiling it as instructed on the user manual but got the message as display below:

kenimor@ubuntu:~/wrf/WRFV3$ export WRF_NMM_CORE=1
kenimor@ubuntu:~/wrf/WRFV3$ export WRF_NMM_NEST=1
kenimor@ubuntu:~/wrf/WRFV3$ ./compile
bash: ./compile: /bin/csh: bad interpreter: No such file or directory

---

