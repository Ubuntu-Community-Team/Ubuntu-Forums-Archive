---
title: "OpenVPN not working with Microsoft's MFA authentication"
date: 2024-09-02
forum: Networking &amp; Wireless
---

### Post by iibarbia on 2024-09-02
Hello,


Since new versions of OpenVPN were released to fix vulnerability CVE-2024-5594 ([https://ubuntu.com/security/CVE-2024-5594](https://ubuntu.com/security/CVE-2024-5594)), we cannot connect via OpenVPN if we use Microsoft's MFA authentication.


The OpenVPN community has recognized the bug and has fixed it in version 2.6.12 ([https://github.com/OpenVPN/openvpn/blob/v2.6.12/Changes.rst](https://github.com/OpenVPN/openvpn/blob/v2.6.12/Changes.rst)): *the fix for CVE-2024-5594 (refuse control channel messages with nonprintable characters) was too strict, breaking user configurations with AUTH_FAIL messages having trailing CR/NL characters. This often happens if the AUTH_FAIL reason is set by a script. Strip those before testing the command buffer (Github: #568). Also, add unit test.*


But this fix has not been uploaded to the Ubuntu repositories yet. Do we know if the fix is &#8203;&#8203;planned to be uploaded to the Ubuntu repositories?


Thanks in advance

---

