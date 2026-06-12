---
title: "Problem with DSL connection (xubuntu 13.10) - &quot;strange&quot; procedure"
date: 2013-11-21
forum: Networking &amp; Wireless
---

### Post by Matteo_Pizzico on 2013-11-21
Hi everybody,
Yesterday I had some problems with the connection on linux (xubuntu), it was slow, I have partly solved by following this guide [http://help.ubuntu-it.org](http://help.ubuntu-it.org).
it said to follow this procedure:

**To configure the modem:**
    Open Applications -> Accessories- > Terminal

    In the terminal type:

    ```
sudo pppoeconf
```

    A text based will guide you for the next steps:

        Confirma of the presence of the ethernet card

        Enter the user name .

        IEnter your password .

         If you already have a PPPoE connection , you are asked if you modify it.

        Popular options : you are asked if you want the options " noauth " and " defaultroute " and if you want to remove " nodetach ." Choose Yes.

        Use peer DNS. Choose Yes.

        Limited MSS problem . Choose Yes.

        When prompted to activate the connection at startup , it is recommended to agree .

        Finally, it asks whether the connection immediately .

    Once you have completed these steps, your connection should be working.

To start your ADSL connection at any time , in a terminal , type:

```
sudo pon dsl-provider
```

To end the ADSL connection, in a terminal , type:

```
sudo poff dsl-provider
```
-----
From that moment the connection is back to normal. The problem is that now the icon that marks the connection at the top next to the date (ie the two arrows) are off as if I was not connected (although I am). using the network options I tried to configure a DSL network but does not appear in the drop-down menu by clicking on the two arrows.

Can anyone tell me what happened and more importantly, this configuration is correct / safe? To restore the previous configuration, how can I?

Sorry for the verbosity and thank you very much in advance :)

P.S.: forgive my english (I'm Italian)

---

