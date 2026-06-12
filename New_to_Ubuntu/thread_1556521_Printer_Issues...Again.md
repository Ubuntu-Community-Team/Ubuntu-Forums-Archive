---
title: "Printer Issues...Again"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by mrphud on 2010-08-19
Hello,

I am again having issues with my printer. I recently plugged in a Brother 2170W. At first ubuntu would not recognize the computer. I submitted a thread that dealt with that.

Now the issue is ... it won't print even though it recognizes the right printer.

I was finally able to print a test page and out popped the line

"You are using the wrong driver"

So the question is: How do I go about installing the "right" driver?

Any suggestions?

Thanks in advance

---

### Post by earthpigg on 2010-08-19
hi,

openprinting.org is generally the ultimate authority on Linux printing. [here]("http://www.openprinting.org/printer/Brother/Brother-HL-2170W") is their documentation on this printer.


the .ppd files are the 'drivers'.

---

### Post by ajgreeny on 2010-08-19
Brother probably has the best drivers if they are not in the repos, and you can get the .deb drivers from [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html)

You seem to need the lpr and cupswrapper drivers which are here:-
[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brhl2170wlpr-2.0.2-1.i386.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brhl2170wlpr-2.0.2-1.i386.deb&lang=English_lpr)
and:-
[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/cupswrapperHL2170W-2.0.2-1.i386.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/cupswrapperHL2170W-2.0.2-1.i386.deb&lang=English_gpl)

---

### Post by mrphud on 2010-08-20
OK. I found the .ppd file. 

I am not quite sure how to install everything from here.

earthpigg: I read the 'letter to garcia'. It was funny, but a bit ironic that you put it up on a help forum.

I am not against putting the work in, but I am still learning linux and the "easy" instructions were confusing. Maybe it's just late and I should look at it tomorrow.

Thanks for the help

---

### Post by earthpigg on 2010-08-20
> **mrphud said:**
> I am not quite sure how to install everything from here.

system -> admin -> printing

remove the broken printer install

'add' a new printer, use that ppd file. i think it's on the second screen of the add wizard that you get to specify a ppd file.

---

### Post by mrphud on 2010-08-21
I went through the wizard. There is no place to specify the .ppd file.


Update: I found out how to add the .ppd file. You have to do it through the CUPS server using [http://localhost:631]("http://localhost:631")

If you try to do it through the sys->admin->printing you will never get the option to select the custom .ppy file.

Thanks for all the help.

---

### Post by mrphud on 2010-08-21
Just thought I would put up the solved sign.

---

