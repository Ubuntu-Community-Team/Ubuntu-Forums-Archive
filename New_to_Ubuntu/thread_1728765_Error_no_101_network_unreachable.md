---
title: "Error no 101 network unreachable"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by bonda.p on 2011-04-14
I was installing Convirture following the steps on [http://www.convirture.com/wiki/index.php?title=C2_ubuntu_installation]("http://www.convirture.com/wiki/index.php?title=C2_ubuntu_installation") when i got stuck in the following step:

sudo ./convirt-install/install/cms/scripts/install_dependencies
[sudo] password for pre: 
install common functions sourced.
DISTRO Ubuntu
VER 10.10
CODENAME maverick
KERNEL 2.6.35-28-generic
ARCH x86_64
Info: Sourcing /home/pre/convirt-install/install/cms/scripts/../../../common/scripts/Ubuntu_functions
Info: Sourcing /home/pre/convirt-install/install/cms/scripts/../common/Ubuntu_functions
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
libxen3 is already the newest version.
python-paramiko is already the newest version.
wget is already the newest version.
dnsmasq is already the newest version.
python-xen-3.3 is already the newest version.
socat is already the newest version.
uml-utilities is already the newest version.
mysql-server is already the newest version.
python-dev is already the newest version.
ssh is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22-generic linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--2011-04-14 00:03:34--  [http://peak.telecommunity.com/dist/ez_setup.py](http://peak.telecommunity.com/dist/ez_setup.py)
Resolving netmon.iitb.ac.in... 10.200.13.50
Connecting to netmon.iitb.ac.in|10.200.13.50|:80... connected.
Proxy request sent, awaiting response... 200 OK
Length: 10240 (10K) [text/plain]
Saving to: `ez_setup.py.10'

100%[==============================================================================================================================>] 10,240      19.7K/s   in 0.5s    

2011-04-14 00:03:42 (19.7 KB/s) - `ez_setup.py.10' saved [10240/10240]

Downloading [http://pypi.python.org/packages/2.6/s/setuptools/setuptools-0.6c11-py2.6.egg](http://pypi.python.org/packages/2.6/s/setuptools/setuptools-0.6c11-py2.6.egg)
Traceback (most recent call last):
  File "ez_setup.py", line 278, in <module>
    main(sys.argv[1:])
  File "ez_setup.py", line 210, in main
    egg = download_setuptools(version, delay=0)
  File "ez_setup.py", line 158, in download_setuptools
    src = urllib2.urlopen(url)
  File "/usr/lib/python2.6/urllib2.py", line 126, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.6/urllib2.py", line 391, in open
    response = self._open(req, data)
  File "/usr/lib/python2.6/urllib2.py", line 409, in _open
    '_open', req)
  File "/usr/lib/python2.6/urllib2.py", line 369, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.6/urllib2.py", line 1170, in http_open
    return self.do_open(httplib.HTTPConnection, req)
  File "/usr/lib/python2.6/urllib2.py", line 1145, in do_open
    raise URLError(err)
urllib2.URLError: <urlopen error [Errno 101] Network is unreachable>
ERROR: Failed installing ez_setup/distutils.


I've checked out all possible solutions to proxy settings(export http_proxy to changing my apt.conf file) but nothing seems to work.

Could someone please help me out? thanks!

---

