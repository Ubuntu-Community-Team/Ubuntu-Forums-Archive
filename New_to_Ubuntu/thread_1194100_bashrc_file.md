---
title: "bashrc file"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by shaheru on 2009-06-22
Hello,
I would like to run a program (./contrib/multibuild.sh) which is under 
shaheru:~/ROI_PAC/ROI_PAC_3_0_1beta3/ROI_PAC$
To run this programme I need to create a path for two libraries (fftw3.h,...): 
export FFTW_LIB_DIR=/home/shaheru/ROI_PAC/ROI_PAC_3_0_1beta3/ROI_PAC/NetInst/fftw-090609-1148/include
export FFTW_LIB_DIR=/home/shaheru/ROI_PAC/ROI_PAC_3_0_1beta3/ROI_PAC/NetInst/fftw-090609-1148/lib

So I  had a blank .bashrc file that is in "shaheru" directory in which I paste the two lines "export". (should I write something else inside the bashrc file??)

Then when I run the multibuild.sh programme, I have the following message:

:~/ROI_PAC/ROI_PAC_3_0_1beta3/ROI_PAC$ ./contrib/multibuild.sh
Will configure using /home/shaheru/ROI_PAC/ROI_PAC_3_0_1beta3/ROI_PAC/configure
FFTW_INC_DIR needs to be set to directory containing fftw3.h

I am still missing the point for this path,
I hope someone can help me,
Thank you!

---

### Post by decoherence on 2009-06-22
the lines

```
export FFTW_LIB_DIR=/home/shaheru/ROI_PAC/ROI_PAC_3_0_1beta3/ROI_PAC/NetInst/fftw-090609-1148/include
export FFTW_LIB_DIR=/home/shaheru/ROI_PAC/ROI_PAC_3_0_1beta3/ROI_PAC/NetInst/fftw-090609-1148/lib
```

assign FFTW_LIB_DIR twice, with the second over-writing the first.

My guess is that it should actually read

```
export FFTW_INC_DIR=/home/shaheru/ROI_PAC/ROI_PAC_3_0_1beta3/ROI_PAC/NetInst/fftw-090609-1148/include
export FFTW_LIB_DIR=/home/shaheru/ROI_PAC/ROI_PAC_3_0_1beta3/ROI_PAC/NetInst/fftw-090609-1148/lib
```

---

### Post by shaheru on 2009-06-22
Still the same error message. Does the bashrc file need to contain other lines? 
Mine is empty and contains only the two described lines. Is it correct to put this .bashrc file in the home directory?

---

### Post by decoherence on 2009-06-22
First.... you started up a new shell after making the changes to bashrc, right? If not, make the changes, then open a new shell. Making changes to bashrc won't effect the running shell unless you explicitly tell it to reload its configuration ("source ." or something like that) -- easiest just to start up a new one.

Now, assuming this isn't the problem...

> **shaheru said:**
> Still the same error message. Does the bashrc file need to contain other lines? 
Mine is empty and contains only the two described lines. Is it correct to put this .bashrc file in the home directory?

Whether the bashrc needs more lines depends on what it's supposed to be doing. From what you've posted, I can't see anything else that needs to be added. If you're asking whether you need a #!/bin/bash or somesuch magic, the answer is no.

Yes, it is correct to put .bashrc in your home directory.

Assuming this isn't the problem, could you try 

```
ls -l $FFTW_INC_DIR/fftw3.h

```
This should print out "fftw3.h" along with some other information. If you get an error, then perhaps this is not the right include directory or perhaps there is a typo in the first line.

---

### Post by shaheru on 2009-06-25
[FONT=Arial][SIZE=2]Thanks for your mail and sorry for the late answer. It was an error in the file name, my fault! I finally wrote the export lines directly in the shell and it works well. Therefore I don' t know if the bashrc file is necessary ?

[/SIZE][/FONT]

---

