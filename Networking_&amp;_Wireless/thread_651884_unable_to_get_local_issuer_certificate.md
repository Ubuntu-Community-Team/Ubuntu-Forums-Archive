---
title: "unable to get local issuer certificate"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by viniciusandre on 2007-12-28
Whenever I try to download a Firefox extension with the automate installer, it keeps waiting, and waiting, and waiting....

If I try to download the file with wget for example (in portuguese):
```
vinicius@vinicius:~$ wget https://addons.mozilla.org/en-US/firefox/downloads/file/18646/fireftp-0.97.1-fx.xpi
--20:35:26--  https://addons.mozilla.org/en-US/firefox/downloads/file/18646/fireftp-0.97.1-fx.xpi
           => `fireftp-0.97.1-fx.xpi'
Resolvendo addons.mozilla.org... 63.245.209.31
Conectando a addons.mozilla.org|63.245.209.31|:443... conectado.
ERRO: Erro na verificação do certificado para addons.mozilla.org: unable to get local issuer certificate
Para conectar à addons.mozilla.org de forma não segura, use `--no-check-certificate'.
Não foi possível estabelecer conexão segura (SSL).

```

It fails to verify the certificate to addons.mozilla.org.
That's ok. As the prompt ask, I always do.

```
vinicius@vinicius:~$ wget --no-check-certificate https://addons.mozilla.org/en-US/firefox/downloads/file/18646/fireftp-0.97.1-fx.xpi
--20:35:52--  https://addons.mozilla.org/en-US/firefox/downloads/file/18646/fireftp-0.97.1-fx.xpi
           => `fireftp-0.97.1-fx.xpi'
Resolvendo addons.mozilla.org... 63.245.209.31
Conectando a addons.mozilla.org|63.245.209.31|:443... conectado.
AVISO: Erro na verificação do certificado para addons.mozilla.org: unable to get local issuer certificate
HTTP requisição enviada, aguardando resposta... 302 Found
Localização: http://releases.mozilla.org/pub/mozilla.org/addons/684/fireftp-0.97.1-fx.xpi [seguinte]
--20:35:53--  http://releases.mozilla.org/pub/mozilla.org/addons/684/fireftp-0.97.1-fx.xpi
           => `fireftp-0.97.1-fx.xpi'
Resolvendo releases.mozilla.org... 32.1.4.248, 2001:4f8:0:2::1f
Conectando a releases.mozilla.org|32.1.4.248|:80... 
```

The same error again, and keeps connecting until the connection timeout.

I have no idea what's happening with my certificates, Tried lots of stuff like purging firefox and reinstalling it again and deleting my personal configuration files under ~/.mozilla folder.
This is a fresh Ubuntu 7.10 installation.

It's terrible to be without my extensions. :(

---

### Post by ifireball on 2007-12-29
I can't read portuguese... 

run the following command in terminal:
```
export LC_ALL=C
```
Then run the *wget* command again _in the same terminal_ it should give you messages in English.

Also please give us some details about how your computer is connected to the internet, are you using a router? some kind of wireless network? do you have a firewall installed on your computer?

---

### Post by viniciusandre on 2007-12-29
Sorry by that. The error messages were in english, but that's a good tip to keep posting my terminal outputs here.  :)

Here you are:
```
vinicius@vinicius:~$ wget --no-check-certificate https://addons.mozilla.org/en-US/firefox/downloads/file/18646/fireftp-0.97.1-fx.xpi
--00:08:44--  https://addons.mozilla.org/en-US/firefox/downloads/file/18646/fireftp-0.97.1-fx.xpi
           => `fireftp-0.97.1-fx.xpi'
Resolving addons.mozilla.org... 63.245.209.31
Connecting to addons.mozilla.org|63.245.209.31|:443... connected.
WARNING: Certificate verification error for addons.mozilla.org: unable to get local issuer certificate
HTTP request sent, awaiting response... 302 Found
Location: http://releases.mozilla.org/pub/mozilla.org/addons/684/fireftp-0.97.1-fx.xpi [following]
--00:08:49--  http://releases.mozilla.org/pub/mozilla.org/addons/684/fireftp-0.97.1-fx.xpi
           => `fireftp-0.97.1-fx.xpi'
Resolving releases.mozilla.org... 32.1.4.248, 2001:4f8:0:2::1f
Connecting to releases.mozilla.org|32.1.4.248|:80... 
```

I'm connected through a wired DHCP network directly to a modem, no router, no proxy, no firewall.

---

### Post by viniciusandre on 2007-12-29
I tried to ping addons.mozilla.org from a different computer on the same network. The another computer can normally download and install the extensions.

Output from my Ubuntu 7.10:
```
vinicius@vinicius:~$ ping addons.mozilla.org
PING addons.glb.mozilla.com (63.245.209.31) 56(84) bytes of data.
```

Output from the Windows XP:
```
C:\Documents and Settings\Administrador>ping addons.mozilla.org
PING addons.glb.mozilla.com [63.245.209.31] 32 bytes de datos:
```

Both outputs successfully ping addons.mozilla.org in the same IP and with data answer. :(

---

