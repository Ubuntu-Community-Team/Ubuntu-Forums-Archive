---
title: "sending email through smtp"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by rosegal on 2010-01-07
hi there..i want to send email using c code through smtp...now i dont actually understand where to start..i think all the other reference i saw is advanced since i am totally new to this...i wanted to know the steps..what should i do first?like should i install smtp server or client? and postfix? what else?Can anyone help me out in this? i don't know if i am on the right track.....Please help...

---

### Post by firefly2442 on 2010-01-07
Do you want to program an email client in C (the programming language) or do you just want to setup an email server to send and receive email?  I'm unsure if this is a programming question or an email server question.

---

### Post by donato roque on 2010-01-07
Is this a server or a desktop?

---

### Post by lotharmat on 2010-01-07
Postfix is a good smtp program - Very easy to set up.

IIRC if you are wanting to use a c prog to send mail; you can just drop the email to a folder and postfix will route it correctly dependant on your settings.

---

### Post by rosegal on 2010-01-08
mr.firefly..my question is sort of programming quest..m new here so,is it posible for me to do both?

Can i know what IIRC stands for?

---

### Post by mlentink on 2010-01-08
Uhhh
Do you want to write your own smtp server?
Or do you just want to make use of one?
Or maybe you want to write a program that allows its users to send mail?

It would help if you could explain just what it is you want to achieve with your program.

In any case, it couldn't hurt to read up on the smt-protocol: [http://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol](http://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol)


[Edit]: IIRC = _**I**_f _**I**_ ***R***emember _**C**_orrectly

---

### Post by rosegal on 2010-01-08
Mr.mlentink...i would go for the 3rd option..to write program that allows user to send email through it...any solution or references would be appreciated...thank u...

---

### Post by mlentink on 2010-01-08
Hmm.

I'm not much of a programmer, and don't know any c at all. What I would try to do first is to have my program invoke an e-mail-client such as Thunderbird, or maybe sendmail (but as far as I know, that implies Postfix). Personally, I wouldn't want to mess with mail-protocols at all. That way, you would only have to catch and temporarily store stuff like to-adresses and a body text and then pass that on to the mail-handler.

Are you sure you want to do it in c? I guess this shouldn't be to hard to do in php on a lamp server with sendmail or Postfix installed.

---

### Post by shortrun on 2010-01-08
rosegal
I am new to all this and have a question that if someone will answer, it will help me and hopefully help you.
 
I want to send pictures, taken automatically from my webcam while I am not at home, via Email to me.  I have a DSL connection to my home so it is allways on.
 
The automatically taking of the pictures I have figured out.
 
I have been experimenting with PHP which I have working on my computer at home along with apache2 and mysql.  ( people call this setup LAMP) All this works, I can write little PHP5 programs, run them and they appear on my FireFox page.
If I wanted the world to see my web page I would need to ?? (I'm not there yet)
 
But I really don't understand mailing.  Can I really just have my computer setup the way I have it, and it can send mail?  Do I need to have something (I don't know what) setup where I have an account with some internet provider?
 
This might be completely obvious but I have not seen it explained anywhere.

---

### Post by rosegal on 2010-01-08
Mr.mlentink..i choose c jst  because i only know about this programming language  but i m not an expert..mayb i can try as u say php..i have seen some examples on it on the net but not sure how to use them..

hope shortrun will get reply which can help me somehow...

Thanks...

---

