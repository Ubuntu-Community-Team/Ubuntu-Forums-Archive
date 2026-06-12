---
title: "Assitance required to install 4in1 Samsung SCX-4824FN"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by kevinAllan on 2010-03-29
I've purchased a new Samsung SCX-4824FN (4-in-1)  printer. I can print but I can't scan. The CD user guide tells me that I must download UnifiedLinuxDriver.tar.gz - which I've done.  I've used Archive Manager to extract and I've also used the command line

[LIST]
[*]tar xzvf UnifiedLinuxDriver.tar.gz to extract.
[/LIST]
One directory called cdroot and one file called install.sh.  None of these have worked.

Could you please assist in helping me to install this 4-in-1.

---

### Post by mikeyphi on 2010-03-30
> **kevinAllan said:**
> I've purchased a new Samsung SCX-4824FN (4-in-1)  printer. I can print but I can't scan. The CD user guide tells me that I must download UnifiedLinuxDriver.tar.gz - which I've done.  I've used Archive Manager to extract and I've also used the command line

[LIST]
[*]tar xzvf UnifiedLinuxDriver.tar.gz to extract.
[/LIST]
One directory called cdroot and one file called install.sh.  None of these have worked.

Could you please assist in helping me to install this 4-in-1.

Welcome!

Could you confirm that you tried to run 'install.sh' via a terminal as root?
To clarify: did you open a terminal, navigate to where the install.sh file is and then type install.sh (return)?

---

### Post by caravel on 2010-03-30
Make the script executable first (as root):

```
chmod a+x install.sh
```

Then execute it from the terminal (also as root):

```
./pathtoscript/install.sh
```

If it errors, post any output here.

---

### Post by dirk_k on 2010-05-04
Update for future references: I got a reply from Kevin that he got the scanner working, whereas the printer should definitely work.

---

### Post by dreych on 2010-11-10
I can't scan in ubuntu 10.04 :(
print working well.
help me plz.

---

### Post by kevinAllan on 2010-11-13
I had the same problem at some stage.  But I un-installed Unified Driver and then re-installed it and it is working.

---

### Post by dreych on 2010-11-14
How exacly you do this? plz write me. with command for run in terminal. and give plz link for driver.

---

