---
title: "password"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by rbee on 2009-11-05
ubuntu 9.10-----I can sign in to ubuntu with name/password but with the same name/password i cannot sign into "terminal".  I have changed name/password but the same thing happens.  How can i get to use terminal?

---

### Post by phillw on 2009-11-05
> **rbee said:**
> ubuntu 9.10-----I can sign in to ubuntu with name/password but with the same name/password i cannot sign into "terminal".  I have changed name/password but the same thing happens.  How can i get to use terminal?

terminal signs you in automatically as who you are...

Applications --> Accesories --> Terminal

you will see the ```
$
``` at the end of your computer name and your name ...

That's you !!!

You are then at the command line.

Phill.

---

### Post by cranecreek on 2009-11-05
As you may or not know the root account is protected in Ubuntu.  If your looking to do something that requires root privileges then do this:
sudo then the comand for what you want to do.
You will be prompted for your user password. Enter that and your command will be executed.

If you need more help try describing what it is your trying to accomplish.

---

### Post by rbee on 2009-11-06
i know my name shows when in terminal but  why doesn't terminal accept my password----same one i use to sign into ubuntu

---

### Post by rbee on 2009-11-06
i am trying to get into terminal using my sign in password but to no avail

---

### Post by sisco311 on 2009-11-06
Do you get any error messages?

---

### Post by Jr.Muffin on 2009-11-06
> **rbee said:**
> i am trying to get into terminal using my sign in password but to no avail

What command are you typing in?

You don't need to login to use the Terminal. To run the Terminal go to "Applications -> Accessories -> Terminal". If you need to do anything which requires root permission, you will need to type "sudo" before the command.

For example: "**sudo** apt-get install midori"

The command I want to run is "apt-get install midori" which installs Midori. To install any software you need root permission. That's why I typed **sudo** before my command so all together it becomes "sudo apt-get install midori".

Once you type sudo and the command, it will ask you for your password. Once you type in your password, it will run the command.

---

### Post by wwwphil on 2010-01-27
> **Jr.Muffin said:**
> What command are you typing in?

You don't need to login to use the Terminal. To run the Terminal go to "Applications -> Accessories -> Terminal". If you need to do anything which requires root permission, you will need to type "sudo" before the command.

For example: "**sudo** apt-get install midori"

The command I want to run is "apt-get install midori" which installs Midori. To install any software you need root permission. That's why I typed **sudo** before my command so all together it becomes "sudo apt-get install midori".

Once you type sudo and the command, it will ask you for your password. Once you type in your password, it will run the command.

I'm having the same problem, I type in 
sudo add-apt-repository ppa:jonoomph/openshot-edge
sudo apt-get update
sudo apt-get install openshot openshot-docs

I'm then asked for my password, when I try to type it in but the letters/ numbers
don't appear in the terminal.  Any ideas please.

---

### Post by Barrucadu on 2010-01-27
> **wwwphil said:**
> I'm having the same problem, I type in 
sudo add-apt-repository ppa:jonoomph/openshot-edge
sudo apt-get update
sudo apt-get install openshot openshot-docs

I'm then asked for my password, when I try to type it in but the letters/ numbers
don't appear in the terminal.  Any ideas please.

Your password is being entered. Nothing appears on screen so people can't see the length of your password.

---

### Post by halitech on 2010-01-27
when typing in your password nothing shows up, just type it in and press enter. It's designed that way as a security feature to prevent people from looking over your shoulder and seeing how many characters are in your password

---

