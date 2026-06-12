---
title: "How to setup a rule for evolution to execute a command when certain email arrives."
date: 2009-12-18
forum: New to Ubuntu
---

### Post by hovzio on 2009-12-18
hi, outlook express has this neat option in which you can setup a filter to have a custom command executed when an email is recieved. Example, an email is recieved from user joe and the email's subject is "SHUTDOWN", you can then setup outlook to filter all incoming mail and to run shutdown.exe anytime a mail with subject "SHUTDOWN" is recieved. (You have to make outlook check for emails every so often.) Can evolution be setup to do this? It would be neat to have a series of commands setup for various simple tasks, and of course your filter for the halt command should be a little more obscure that "SHUTDOWN".. ;) Appreciate any help in advance.

Thanks, hovzio :)

---

### Post by Cuco3 on 2009-12-18
You should be able to.

Try going to evolution, click on said-account's inbox, go to the Message > Create Rule > Filter on Subject. You'll be presented with a box that'll look something like this:

[IMG]http://img51.imageshack.us/img51/341/tempxx.png[/IMG]

Configure it the way you want. Remember that the "shutdown" program is found in /sbin

After you finish there, go to Edit > Preferences. Click "Edit" for the e-mail account that you specified the filter for. Go to the "Receiving Options" tab and click "Apply filters to new messages in inbox on this server"

---

### Post by hovzio on 2009-12-19
> **Cuco3 said:**
> You should be able to.

Try going to evolution, click on said-account's inbox, go to the Message > Create Rule > Filter on Subject. You'll be presented with a box that'll look something like this:

[IMG]http://img51.imageshack.us/img51/341/tempxx.png[/IMG]

Configure it the way you want. Remember that the "shutdown" program is found in /sbin

After you finish there, go to Edit > Preferences. Click "Edit" for the e-mail account that you specified the filter for. Go to the "Receiving Options" tab and click "Apply filters to new messages in inbox on this server"

very cool, thank you! I actualy got the whole part except the part where you apply filters in the prferences. Thank you! :)

---

