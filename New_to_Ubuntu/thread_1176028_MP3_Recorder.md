---
title: "MP3 Recorder"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by daniell59 on 2009-06-01
Can someone recommend a basic MP3 recorder that is compatible with Ubuntu?

Thanks

---

### Post by Bradtek on 2009-06-01
Applications / Sound & Video / Sound Recorder

If you haven't already done so install ubuntu-restricted-extras to have mp3 and other non free codecs installed

---

### Post by daniell59 on 2009-06-01
> **Bradtek said:**
> Applications / Sound & Video / Sound Recorder

If you haven't already done so install ubuntu-restricted-extras to have mp3 and other non free codecs installed

Thanks, how do I intall ubuntu-restricted-extras?

---

### Post by Steelmourne on 2009-06-01
Don't use mp3. Use .ogg. Patent free and better quality at higher bitrates (256kb/s). Also takes up less space. For that I'd use grip.

---

### Post by oldos2er on 2009-06-01
> **daniell59 said:**
> Thanks, how do I intall ubuntu-restricted-extras?

 Open a terminal and enter
```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

---

### Post by daniell59 on 2009-06-01
> **oldos2er said:**
> Open a terminal and enter
```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

I am stuck here. What do I do?

its subject matter.  It supersedes all prior or contemporaneous       &#8593; 
 &#9474;     oral or written communications, proposals, representations and        &#9618; 
 &#9474;     warranties and prevails over any conflicting or additional terms      &#9618; 
 &#9474;     of any quote, order, acknowledgment, or other communication           &#9618; 
 &#9474;     between the parties relating to its subject matter during the term    &#9618; 
 &#9474;     of this Agreement.  No modification of this Agreement will be         &#9618; 
 &#9474;     binding, unless in writing and signed by an authorized                &#9618; 
 &#9474;     representative of each party.                                         &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; For inquiries please contact: Sun Microsystems, Inc., 4150 Network        &#9618; 
 &#9474; Circle, Santa Clara, California 95054, U.S.A.                             &#9618; 
 &#9474;                                                                           &#9646; 
 &#9474; DLJ v1.1                                                  27APR2006ANS    &#8595; 
 &#9474;

---

### Post by Steelmourne on 2009-06-01
That is probably the Java license agreement. Hit TAB to select OK to continue.

---

### Post by john.nicholls on 2009-06-01
There should be an "Accept" button. Click on it.

---

### Post by antmenj on 2009-06-02
If its recording software you want try audacity.  It can export ogg and mp3.  Ogg does sound better for the file size.

---

### Post by daniell59 on 2009-06-02
> **antmenj said:**
> If its recording software you want try audacity.  It can export ogg and mp3.  Ogg does sound better for the file size.

How do I download Audacity on Ubuntu. I could never get it to work in Vista. I am willing to give it another try.

Thanks

---

### Post by Sef on 2009-06-02
> How do I download Audacity on Ubuntu. I could never get it to work in Vista. I am willing to give it another try.

Applications > Add/Remove > Show: All Available Applications > Search: Audacity > tick box next to Audacity > apply changes > apply > close

---

### Post by billgoldberg on 2009-06-02
> **daniell59 said:**
> How do I download Audacity on Ubuntu. I could never get it to work in Vista. I am willing to give it another try.

Thanks

The same way you install anything else on Ubuntu.

Use the package managers (add/remove, synaptic or apt-get).

---

### Post by daniell59 on 2009-06-02
Someone Please tell me what is going on, and how to remedy it.

Thanks

---

### Post by oldos2er on 2009-06-02
What were you doing before that error msg came up?

---

### Post by oldos2er on 2009-06-02
> **john.nicholls said:**
> There should be an "Accept" button. Click on it.

 The ncurses interface for the Java EULA is not mouseable. Use Tab, arrow keys, and Enter instead.

---

### Post by daniell59 on 2009-06-02
> **oldos2er said:**
> What were you doing before that error msg came up?

I kept trying to hit the ok button. Nothing happened. I finally shut it down, and called it quits for the night.

---

### Post by oldos2er on 2009-06-02
Try running **sudo dpkg --configure -a**

---

### Post by daniell59 on 2009-06-02
> **oldos2er said:**
> Try running **sudo dpkg --configure -a**

Ran it, with this result

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
daniel@daniel-desktop:~$

---

### Post by daniell59 on 2009-06-02
By typing sudo apt-get -f install I was able to complete the installation of the program.

---

### Post by antmenj on 2009-06-02
> **daniell59 said:**
> How do I download Audacity on Ubuntu. I could never get it to work in Vista. I am willing to give it another try.

Thanks

I'v used it on someone else's XP machine and on Dapper without problems.

It seems popular in Hardy.

---

