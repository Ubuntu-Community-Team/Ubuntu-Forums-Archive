---
title: "Accounting Package"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by expatCM on 2009-06-01
Does anyone have suggestions for accounting systems / order processing?

I have been asked to make suggestions for a small company.  Three offices.  Internet in only two.  The need is to process orders / sales transactions and stock transfers between the offices.  The office without Internet could collect data on a laptop and take to the Internet each day for update on a central server.  

Eventually the company would like to be able to move off or broaden the present telephone sales and put up a website to make the selling cycle more accessible and efficient.

The existing setup is memorable.  It is a mess.  One of the best.  But it sort of works.  There is a Windows based accounting server which only the local office can access.  The other offices fax in their data for manual update.  The accounting software is proprietary and quite a lot dated.

The company location is in Thailand.  Language is not really an issue but the cost of closed source accounting packages would be.

So … any ideas very welcome …..

---

### Post by keplerspeed on 2009-06-01
All I have heard of is GNUcash and homebank.. more for just tracking accounts. I have used homebank, more for a personal/home budget, not so much as office accounting. However GNUcash may be a closer option. Has anyone had experience with GNUcash?

EDIT with a wiki search, look at the end of this page [http://en.wikipedia.org/wiki/Accounting_software](http://en.wikipedia.org/wiki/Accounting_software)
or search the page for 'open source'. Ill have a snoop around and see what they are like:

Stand-alone:	
GnuCash · Grisbi · HomeBank · KMyMoney · OpenERP · TurboCASH

Web-based:	
Adempiere · BlueErp · Compiere · EdgeERP · ERP5 · FrontAccounting · IntarS · Openbravo · OpenERP · opentaps · PhreeBooks · WebERP

Also Microsoft Office Accounting Express... but its microsoft.

---

### Post by keplerspeed on 2009-06-01
Ok so by the looks of that, I would say either GNUcash (multi platform) or Turbocash (win only, or in wine), as they both do account keeping, but also some small business processes. Let me know how you go.

---

### Post by Didius Falco on 2009-06-01
Here are four possibilities - I found these doing a little google-fu, so don't take this as a recommendation, just possibilities:

[http://www.shcircuit.com/~ross/]("http://www.shcircuit.com/%7Eross/")

[http://www.linuxcanada.com/](http://www.linuxcanada.com/)

[http://www.sql-ledger.com/](http://www.sql-ledger.com/)

[http://www.appgen.com/site/mybooks_professional.htm](http://www.appgen.com/site/mybooks_professional.htm)

I hope it helps...

Regards,

Didius

---

### Post by expatCM on 2009-06-01
Both GnuCash and Homebank from the descriptions in Synaptic and on the web pages appear to be really home financial management / personal wealth management solutions ....  Not so good for company trading.

Quasar is an interesting example.  Good for the wealth of Canada and the States no doubt but would not get off the ground here ....  just too expensive.

MyBooks sort of starts off fine with the price of a single seat but the additional seats make very little sense when you compare the cost with that of local labor prices.

SQL-Ledger looks interesting ....  need to explore a bit more.

I see some mention of ERP.  I am not very familiar with the extent of ERP solutions but would it be better to look at this as a bigger picture solution?

---

### Post by expatCM on 2009-06-01
Does anyone have hands on experience here?  Search engine recommendations are fine but has anyone actually done it?

---

### Post by HereInOz on 2009-06-01
I have run TurboCash on Linux using Wine, and it runs quite well and reliably.  

It is actually quite a tidy system and I would be using it except for one thing, and that is that I often receive goods from an order on more than one invoice - back orders, that sort of thing, and TurboCash does not allow the recording of more than one supplier's invoice number against one purchase order.  Bit sad, really.

TurboCash 4 does not, to my knowledge, run with Wine; you will need TurboCash 3.x for that application.

---

### Post by plavania on 2010-06-15
Please visit the Blog section of Walking Tree on "How To's" of Adempiere. Walking Tree has extensive experience in Adempiere and built there own ERP product EagleRP on top of Adempiere. They have a strong presence in ERP Implementation and Customizations around Adempiere, for more than 4 years now with a clientele from different verticals. By end of 2010, the company is publishing a book on "How To's" for Adempiere to make life easier for all fellow implementers.
Incase you do not find the information that you are looking for already existing on their blog, try posting a question, and you can be assured of a prompt and overwhelming reply.
[http://www.walkingtree.in](http://www.walkingtree.in)
[http://wtcindia.wordpress.com/](http://wtcindia.wordpress.com/)

---

### Post by Zlatan on 2010-08-08
> **expatCM said:**
> Does anyone have suggestions for accounting systems / order processing?

I have been asked to make suggestions for a small company.  Three offices.  Internet in only two.  The need is to process orders / sales transactions and stock transfers between the offices.  The office without Internet could collect data on a laptop and take to the Internet each day for update on a central server.  

Eventually the company would like to be able to move off or broaden the present telephone sales and put up a website to make the selling cycle more accessible and efficient.

The existing setup is memorable.  It is a mess.  One of the best.  But it sort of works.  There is a Windows based accounting server which only the local office can access.  The other offices fax in their data for manual update.  The accounting software is proprietary and quite a lot dated.

The company location is in Thailand.  Language is not really an issue but the cost of closed source accounting packages would be.

So … any ideas very welcome …..

would go with opentaps, check [this]("http://opentaps.org/products/online-demo")

---

### Post by jaya28inside on 2010-09-09
i did chose WEBERP... but no tutorial found within our forums
is there anyone would like to post it up "WEBERP-HOW-TO" installation for Debian, this?

* I thought not many users used WEBERP. is it, wrong?

---

### Post by techmoz on 2010-09-21
> **expatCM said:**
> Both GnuCash and Homebank from the descriptions in Synaptic and on the web pages appear to be really home financial management / personal wealth management solutions ....  Not so good for company trading.

Quasar is an interesting example.  Good for the wealth of Canada and the States no doubt but would not get off the ground here ....  just too expensive.

MyBooks sort of starts off fine with the price of a single seat but the additional seats make very little sense when you compare the cost with that of local labor prices.

SQL-Ledger looks interesting ....  need to explore a bit more.

I see some mention of ERP.  I am not very familiar with the extent of ERP solutions but would it be better to look at this as a bigger picture solution?
I am trying to install SQL-Ledger on Ubuntu 10.04 server and what a nightmare. I installed the version that is on synaptic and and could not see local host. I downloaded the setup.pl and followed the instructions to install on /usr/local/sql-ledger. run well but on trying to get the local host I keep getting/ downloading a plain .pl text file. Where am I going wrong? somebody help

---

