---
title: "Apache wont mail php forum?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by justinram22 on 2009-04-13
Hello, this is probably the wrong forum to post this topic on, but please bare with me :) .  Ok, my problem is that i create a php forum, such as

[PHP]
<php?

   $to = myemail@email.com;
   $subject = "Test";
   $message = "Message test";
   mail($to, $subject, $message);
?>
[/PHP]

This does not send it to my email for some reason.  Is there a config that i need to edit in apache to allow mail to send?  Any help would be greatly appreciated!

---

### Post by aaronp on 2009-04-13
Is this a local apache server on your system or a webhost?

If it is local, it will use your sendmail configuration to send the mail. If that is not set up correctly then this is likely your problem.

If it is on a host then you need to have smtp support on the domain that you are using.

I find the best way to get around both of these issues if thre is no easy solution is to use the PEAR php mail package and just use a gmail or your ISP smtp server.

Aaron

---

