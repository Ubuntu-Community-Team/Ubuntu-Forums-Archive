---
title: "Opening a terminal on a different machine?"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by zcacogp on 2010-05-13
Chaps, 

I have no idea how difficult the question I am about to ask is, but I'll ask it anyway ... 

I can open a terminal on the machine I am on (x61s). 

I can open a terminal on any one of the other two machines I own (desktop and x31s). 

How hard is it to open a terminal on another machine, on the machine I am on? (As in, when I am sitting at the x61s machine, to open a terminal with the prompt "ogp@xdesktop:~$" - I am ogp.) 

I am a bit of a beginner, so please explain things carefully .... sorry!


Oli. 

P.S. All machines are running 10.4 lucid.

---

### Post by cariboo on 2010-05-13
You can use ssh if the other systems are running a Linux variant. You will have to install openssh-server on all machines, then simply open a terminal and type:

```
ssh user@computer
```

this will open a terminal on another computer. For more info on setting up ssh have a look [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys").

---

### Post by zcacogp on 2010-05-13
cariboo, 

Thanks. For the suggestion and the link. 

I installed openssh-server, but it didn't work. That's to say that the server installed fine, but I couldn't connect from one machine to the other. Either from desktop to x31 or back. The error was always "Host key verification failed."

What have I done wrong? (The network is simple - just two - or three - machines, and I have done none of the security stuff suggested in the article. But the article suggests it should be possible without the security stuff ... ) 

Thanks for your help, and for any further assistance!


Oli.

---

### Post by zcacogp on 2010-05-14
Ummm, OK. Done a bit more poking around with this one. And made some progress ... 

Slightly embarassed 'cos it was my mistake. In practice, the dialogue involved the following question: 

```
The authenticity of host 'desktop (192.168.10.3)' can't be established.
RSA key fingerprint is <snip>
Are you sure you want to continue connecting (yes/no)?

```
... and I pressed 'return', not realising that this was taken as 'No'. If I type 'yes' then it all works as it should ... 

So, thanks for the advice. It worked, and sorry for being slightly inept in what I did! 


Oli.

---

### Post by spiky001 on 2010-05-14
We all learn

---

### Post by zcacogp on 2010-05-14
Yes. Just some more slowly than others! :(


Oli.

---

