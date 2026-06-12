---
title: "Compiling Packages... General how-to?"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by Twitch04 on 2010-05-12
I've googled all over for help with this. I want to get programs for Ubuntu at school, but I obviously can't bring my OS with me. I know that some places just put the .tar.gz files up for download, and usually these come with a general README file that says...

1.) Extract the .tar.gz file

2.) Navigate to the folder in terminal

3.) type "./compile"

4.) type "make"

5.) type "install"

Or something like that. But I think something goes wrong after the "./compile" part. The README says that after that, it should make some sort of executable file or something, but that never happens. I can't give any details right now because I'm at school, but I can update in roughly 6 hours when I'm back at home with what the terminal says exactly.

So could someone sorta, in the meantime, explain what should happen when you try to do that? Thank you in advance, everyone.

---

### Post by qamelian on 2010-05-12
Step 3 should be:```
./configure
```.

If this step fails, it will usually tell you why, such as missing dependancies. You need to resolve any errors in this step before proceeding.

---

### Post by adam22 on 2010-05-12
You may not have the tools necessary to compile the source...what programs are you wanting that is only available in a tarball, though? Most come in .debs or have a repository....

See [this](https://help.ubuntu.com/community/CompilingEasyHowTo).

---

### Post by shebaw on 2010-05-12
This helped me out, [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

I googled something to compile from source and found nmap. I compiled it yesterday and it was my first time compiling from source. I felt like a hacker the whole day :lolflag:

---

