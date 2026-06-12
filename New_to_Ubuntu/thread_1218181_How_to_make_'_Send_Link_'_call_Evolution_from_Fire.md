---
title: "How to make ' Send Link ' call Evolution from Firefox"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by rsiddharth on 2009-07-20
I use Firefox(3.5) to Browse the Internet , I have been trying to send links to friends by email through Firefox's ' Send Link ' option , but unfortunately I don't know the way to configure the Firefox to open the Compose box of Evolution with the desire linked placed in the message box of the Evolution Compose Window . :confused: 

Thanks for your help .

---

### Post by zebsdad on 2009-07-20
Go to Evolution program and set it as default?

---

### Post by BDNiner on 2009-07-20
I thought that evolution was the default mail application and the send to link would open evolution. But just go to program defaults and set the mail application to default. I have mine set to Thunderbird and it works quite well. only gripe is if i have have thunderbird open then it does not work.

---

### Post by y-lee on 2009-07-20
Setting program defaults don't seem to work for me, i am running ubuntu remix off of a flash drive adn evolution is set as the default e-mail program. But anyway ...

What happens when you click a send mail link? You can [test here]("http://www.w3schools.com/html/tryit.asp?filename=tryhtml_mailto"). If FF has not been configured to handle such links then a **Launch Application** window should pop up click the **choose** button. naviagte to **/usr/bin** and find the evolution file and click it and then click **open.**  be sure the *remember my choice ...* box is checked and then click **ok**.

---

### Post by rsiddharth on 2009-07-20
> **y-lee said:**
> Setting program defaults don't seem to work for me, i am running ubuntu remix off of a flash drive adn evolution is set as the default e-mail program. But anyway ...

What happens when you click a send mail link? You can [test here]("http://www.w3schools.com/html/tryit.asp?filename=tryhtml_mailto"). If FF has not been configured to handle such links then a **Launch Application** window should pop up click the **choose** button. naviagte to **/usr/bin** and find the evolution file and click it and then click **open.**  be sure the *remember my choice ...* box is checked and then click **ok**.
Thank you  y-lee , It worked , as you said the Launch Application appeared ( actually this was the place where I get stuck and prior new nothing to go further than this ) , I chose ' Choose '  went to /usr/bin , found 'evolution' and the next instant the Compose box opened with the URL in the text box! .

---

### Post by rsiddharth on 2009-07-20
zebsdad , Evolution as  BDNiner told is the default email application in ubuntu . Even though I new it was I just doubled checked it and found that Evolution indeed is my default email client. :D

---

