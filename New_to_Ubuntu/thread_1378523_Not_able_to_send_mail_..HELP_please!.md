---
title: "Not able to send mail ..HELP please!"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by Geeking4awhile on 2010-01-11
hi all i am absolutely new to linux /ubuntu.

How to send a mail from command line?
I used the below.The command seems to right.
echo "hi buddy " | mailx -s "Could you please help me" [email]XXXXX@gmail.com[/email]
But i am not getting the mail in my gmail inbox when i check it.
Do i need to set something else in my terminal?
I tried to ask google or searh the forum.
But being a beginner i hardly understand the technical jargons and don't get my exact reply.


Could you please help?

---

### Post by warfacegod on 2010-01-11
Since when can you send email from a Terminal? Why not just use a web browser or set up an email client?

---

### Post by halitech on 2010-01-11
worked for me just fine to both my gmail and my isp mail. do you get any errors when you try? maybe you don't have an MTA (mail transport agent) installed (unlikely) or maybe your ISP is blocking sending mail by any server except theirs.

@warfacegod, maybe the OP is running a server with no gui or just wants to learn the ins and outs of mail sending from the terminal in case the gui dies on them?

---

### Post by Geeking4awhile on 2010-01-11
Thanks for the reply buddy!
Could you pleaselet me know how to check whether MTA is working or not.
If its not working how to make it work/install?
No i don't get any error while i try.
It returns to thecommand prompt as usually.
It even gives the return code 0 when i type 'echo $?'

---

### Post by halitech on 2010-01-11
check in Synaptic and see if there is an MTA installed. I'm not sure which actual package you would want to search for.

Can you use gmails servers to send mail from a mail program?

---

### Post by Geeking4awhile on 2010-01-11
I just finished setting up postfix following the steps given in
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
Still the mail is not working.
I have some confusion in the steps.
1.when it says server1.example.com can i put server1.gmail.com?
2. Can i enter any word of my choice when it prompts me to enter passphrase?
3.As the line says
"If you want to use port 587 as the submission port for SMTP mail rather than 25 (many ISPs block port 25), you will need to edit /etc/postfix/master.cf to uncomment the relevant line for port 587 there."
I  don't find the no 587 anywhere commented neither 25.
4. As per the first step of troubleshooting do i need to set the Configure saslauthd to Default?
I don't know how to use the gmail servers from any command line to send mail.

---

### Post by halitech on 2010-01-11
I'm not an expert in setting up mail servers

1. no because that is only for domains that you own and host yourself

2. yes

3. not sure

4. not sure

try this
```
telnet smtp.mail.yahoo.com 25
```and see if it can make a connection. if it fails, your ISP is probably blocking outgoing access on port 25

---

### Post by dmillerct on 2010-01-11
> **Geeking4awhile said:**
> I just finished setting up postfix following the steps given in
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
Still the mail is not working.
I have some confusion in the steps.
1.when it says server1.example.com can i put server1.gmail.com?
2. Can i enter any word of my choice when it prompts me to enter passphrase?
3.As the line says
"If you want to use port 587 as the submission port for SMTP mail rather than 25 (many ISPs block port 25), you will need to edit /etc/postfix/master.cf to uncomment the relevant line for port 587 there."
I  don't find the no 587 anywhere commented neither 25.
4. As per the first step of troubleshooting do i need to set the Configure saslauthd to Default?
I don't know how to use the gmail servers from any command line to send mail.

Do what Halitech suggests, If you get a response from the server you don't need to change SMTP ports. 

Go to your ISP's website they should have documentation there regarding the name of the SMTP server. Enter that address or IP into the configuration.

---

