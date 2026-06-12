---
title: "Verizon Email using DSL"
date: 2015-04-14
forum: Networking &amp; Wireless
---

### Post by arancher on 2015-04-14
Problem Description
   Prior to this problem, using Verizon for my standard Telephone connection.
   Updated my Telephone line to use DSL in January.
   Received an email address from Verizon.
   DSL part working perfect.
   Since then, I have been trying to get my Email account that I received
      from Verizon to work.
   No success at all

Parameters
   From Verizon and from the Internet, I got the following information:
                 Server             Port  Encryption    Data
     Incoming    pop.verizon.net    995      SSL        Normal Password
     Outgoing    smtp.verizon.net   465      SSL        Normal Password

Clients
   I've tested this in two Mail Clients, Evolution and Thunderbird.
   Basically the same results
      "Authentication Failure on password during POP processing"

Thunderbird
   Email name - [EMAIL="MyUser@verizon.net"]MyUser@verizon.net[/EMAIL]
       When I select "Manual config", it gives the following:
                    Server  hostname  Port    SSL     Authentication
   Incoming   POP3  pop.verizon.net   995   SSL/TLS   Normal password
   Outgoing   SMTP  smtp.verizon.net  465   SSL/TLS   Normal password
   Username   Input  MyUser                Output   MyUser
      when I click "Re-Test" button, it runs fine
      When "Done" button is pressed, get the following message:
     "Configuration could not be verified - is the username or password wrong"
      It creates an account but when I attempt to process the messages
        from the Server at Verizon, it gets the following messages:
         "Sending of password for MyUser did not succeed"
         "Mail Server pop.verizon.net responded: Authentication failed"

Evolution
   It generates an Account successfully using the above values,
  but when I attempt to get any mail from my verizon inbox,
      I get the following messages:
      "Unable to connect to POP server pop.verizon.net"
      "Error sending password ERR [AUTH] authentication failed"

Username and Passwrds are correct since I use them on myverizon and webmail

Environment
    PC running Ubuntu - Precise Pangolin - All up to date
Firewall
   Firewall in NOT active
   sudo ufw status
      Status: inactive
Modem/Router
   My Modem is a Verizon, Westell and has its Firewall set to
     No Security (None)
        all Traffic is allowed

Verizon support is not very effective.  Their personal are fairly hard to
understand due to language differences and very limited in their knowledge,
especially concerning Linux.

Does any one know how to solve this problem or can point me in the
correct direction.

I'm Computer literate and so I can do just about anything that has
to be done in order to fix this problem.

Thanking everyone in advance who takes the time to look at this problem.

Yours truly,

Frank Krauss

---

### Post by Vladlenin5000 on 2015-04-15
Your email isn't really "[EMAIL="MyUser@verizon.net"]MyUser@verizon.net[/EMAIL]", is it?
(I'm assuming it's just an example...)

---

### Post by arancher on 2015-04-16
Your Correct,

That was just a Dummy name I put in for the purpose of writting this note.

Frank

---

