---
title: "Anybody know how to read this file"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by Ralph L on 2010-04-15
I have a file that I got when I downloaded something.  I included the start of it below.  Can anybody tell me what program I can read this with.

Thanks

Ralph

OFXHEADER:100

DATA:OFXSGML

VERSION:102

SECURITY:NONE

ENCODING:USASCII

CHARSET:1252

COMPRESSION:NONE

OLDFILEUID:NONE

NEWFILEUID:NONE



<OFX>

  <SIGNONMSGSRSV1>

    <SONRS>

      <STATUS>

        <CODE>0</CODE>

        <SEVERITY>INFO</SEVERITY>

        <MESSAGE>Signon OK</MESSAGE>

      </STATUS>

      <DTSERVER>20100415173958.315[-7:PDT]</DTSERVER>

      <LANGUAGE>ENG</LANGUAGE>

      <DTPROFUP>20090629112600.000</DTPROFUP>

      <DTACCTUP>20100409120000.000</DTACCTUP>

      <FI>

        <ORG>Credit Union</ORG>

        <FID>322274462</FID>

      </FI>

      <USERS.TYPE>3</USERS.TYPE>

---

### Post by lisati on 2010-04-15
OFX = "Open Financial Exchange"
Have a look here: [http://www.ofx.net/](http://www.ofx.net/)

Edit: I think there are a couple of programs in the repos that can read it, e.g. gnucash, kymoney, grsbi, homebank

---

### Post by Ralph L on 2010-04-19
lisati

Thank you very much.  This was just what I needed.  I would never have figured this out on my own.  I used Synaptic to install Homebank and Gnucash.  Both read my files ok.  Haven't tried to do more yet.

Thank you again

Ralph

---

### Post by Iowan on 2010-04-19
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? =D>

---

