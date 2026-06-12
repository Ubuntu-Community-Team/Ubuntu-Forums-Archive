---
title: "php mail problem"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by Dinu. on 2009-11-29
[B]I have installed and configure postfix mail server.i am able to sent mail through php mail function.but my problem is i cant able to sent all the mail which i declared in $to variable.the mail is delivered to particular email id only pls tell me any solution for this. 
[/B]

---

### Post by bsharp on 2009-11-29
You haven't really given enough information to help us solve your problem. Could you post the code you are working with surrounded by php tags?

---

### Post by Dinu. on 2009-11-30
[B]I have install and configured postfix mail server to send mail through php.
but my problem is.
           coding:
                [/B] <?php 
$to = "dineshsingh_mca@ymail.com"; 
$subject = "Hi!"; 
$body = "Hi,\n\nHow are you?"; 
$from="dinesh_mca@rocketmail.com"; 
$header="from:$from"; 
if (mail($to, $subject, $body,$header)) { 
  echo("<p>Message successfully sent!</p>"); 
 } else { 
  echo("<p>Message delivery failed...</p>"); 
 } 
?>
[B]but when i change $to variable email id as [$to="dinu.284@gmail.com"]i cant able to sent mail to following address.i have tried to other email ids also i cant able to sent them also.
             moreover when i start my system today morning i cant able to sent even mail to above php code.
             i think i have done something wrong in configration. [/B]
      **i even changed in php.ini   sendmail_path = /usr/sbin/sendmail -i -t**
        pls try to slove my problem because i am doing project in lamp and php mail is important module for the project

---

