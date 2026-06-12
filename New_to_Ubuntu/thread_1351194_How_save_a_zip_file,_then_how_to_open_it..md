---
title: "How save a zip file, then how to open it."
date: 2009-12-10
forum: New to Ubuntu
---

### Post by lilithdog on 2009-12-10
Hi, I am trying to unload a zip file named:

[ftp://ftp.cbcb.umd.edu/pub/data/bowt...isiae.ebwt.zip]("ftp://ftp.cbcb.umd.edu/pub/data/bowtie_indexes/s_cerevisiae.ebwt.zip")

It keeps saying no such file or directory.  The bowtie file is on the desktop/bowtie-0.11.3.
so far i am not including that. Do I need to? I am already working out of this directory.

this is supposed to read for the ... part /bowtie_indexes/s_cerevisiae.ebwt.zip

How do i make this work?

Then, any suggestions for unzipping it?

I looked on the forums, but they didn't help.

---

### Post by lilithdog on 2009-12-10
**How save a zip file, then how to open it.** 			
 			 			 		   		 		 		Hi, I am trying to unload a zip file named:

[ftp://ftp.cbcb.umd.edu/pub/data/bowt...isiae.ebwt.zip]("ftp://ftp.cbcb.umd.edu/pub/data/bowtie_indexes/s_cerevisiae.ebwt.zip")

It keeps saying no such file or directory.  The bowtie file is on the desktop/bowtie-0.11.3.
so far i am not including that. Do I need to? I am already working out of this directory.

this is supposed to read for the ... part /bowtie_indexes/s_cerevisiae.ebwt.zip

How do i make this work?

Then, any suggestions for unzipping it?

I looked on the forums, but they didn't help.

---

### Post by Idaho Dan on 2009-12-10
lilithdog, I clicked on your link and it started downloading.
To unzip, right click on it and choose extract here.
I hope this helps.

---

### Post by lilithdog on 2009-12-10
But how do I get this to work from a terminal window?  

Thanks

---

### Post by zigmo on 2009-12-10
Are you trying to upload or download the file?

If you're trying to download, use the following commands:

ftp (enters ftp program)
open 128.8.120.95 (opens connection to server)
user (starts login process)
cd pub/data/bowtie_indexes (moves you to correct directory)
get s_cerevisiae.ebwt.zip (downloads file to your local computer)
bye (when done, exits ftp program)
cd ~ (navigates to your local home directory, where file downloaded)
unzip s_cerevisiae.ebwt.zip (unzips file)

That should do it.

edit: for some reason, I couldn't open an FTP connection to the server via the host name, but the IP address worked fine from the ftp command line.

---

### Post by squaregoldfish on 2009-12-10
I can retrieve the file using wget:

```
wget ftp://ftp.cbcb.umd.edu/pub/data/bowtie_indexes/s_cerevisiae.ebwt.zip
```

Once it's downloaded, you can you unzip to extract it:

```
unzip s_cerevisiae.ebwt.zip
```

Or the file-roller (Archive Manager) application should be able to handle it.

Steve.

---

### Post by oldos2er on 2009-12-10
> **lilithdog said:**
> But how do I get this to work from a terminal window?  

Thanks

 If the file is on your desktop, first run **cd Desktop**

---

### Post by lilithdog on 2009-12-10
oops, wrong posting.

---

### Post by lilithdog on 2009-12-10
**Re: How save a zip file, then how to open it.** 			
 			 			 		   		 		 		I tried this, but once I got to user it said "530 This ftp server is anonymous only"

Thanks though. I have no idea why others can get this to work but I can't.

---

### Post by t0p on 2009-12-10
> **lilithdog said:**
> **Re: How save a zip file, then how to open it.**             
                                                                I tried this, but once I got to user it said "530 This ftp server is anonymous only"

Thanks though. I have no idea why others can get this to work but I can't.


**squaregoldfish** said he successfully downloaded the file by running the command

```
wget ftp://ftp.cbcb.umd.edu/pub/data/bowtie_indexes/s_cerevisiae.ebwt.zip
```
[FONT=monospace]
Are you saying that that command doesn't work for you?
[/FONT]

---

