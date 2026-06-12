---
title: "ssh scripting question"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by Abu_Dayya on 2011-05-21
I have a script where I want to ssh to many server (for loop)and run some commands there. How can I capture the out put of all these ssh sessions on one file?

for example, here is my script ```

ssh -l username 1.2.3.4 <<EOF
command 1 
command 2
command 3
EOF
```

this will display the output on screen, or i can redirect each command to a file like
```
ssh -l username 1.2.3.4 <<EOF
command 1 >> output.txt
command 2 >> output.txt
command 3 >> output.txt
EOF
```

but this will redirect the output to a file on THAT particular server. In my script I want to ssh to many servers, and I want to capture the output on my local workstation. 

Hope this was clear

---

### Post by Lateralis on 2011-05-21
I'm not sure if you can directly save the output to your local machine.  But you could always scp the output file from the remote computer to your local machine?

---

### Post by Abu_Dayya on 2011-05-21
yeah thats true. but our firewall team don't allow it.

I also tried
```
cat commands-list | ssh -l username 1.2.3.4 >> output.txt
```
doesn't work either

---

### Post by compmodder26 on 2011-05-21
run your command in "script".  It should be installed by default.  Use "man script" for usage instructions.

---

### Post by Abu_Dayya on 2011-05-23
Anyways, I talked to the firewall guys, and I am now able to scp the files back.

---

