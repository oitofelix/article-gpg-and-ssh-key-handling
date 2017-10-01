---
title: oitofelix - Article&#58; GPG and SSH key handling
description: >
  The "GPG and SSH key handling" article shows how to handle GPG and
  SSH cryptographic keys for common use cases.  Currently, it covers
  the importing and validation of my public keys.
tags: article, free software, GPG, SSH, PGP, cryptography
license: CC BY-SA 4.0
layout: oitofelix-homepage
base: http://oitofelix.github.io
#base_local: http://localhost:4001
---
<div id="markdown" markdown="1">
## Article: GPG and SSH key handling

This article shows how to handle GPG and SSH cryptographic keys for
common use cases.  Currently, it covers the importing and validation
of my public keys.

- [GPG key handling]({{site.baseurl}}/#gpg-key)
- [SSH key handling]({{site.baseurl}}/#ssh-key)


### GPG key

You can use my public GPG key for encrypting data you want to
send to me privately and to check the authenticity of my
signature in emails and tarball releases, for example.  There
are three main ways of obtaining my public GPG key:

1. Using browser's inline GPG handling capabilities.
   [Try it!]({{site.baseurl}}/#browser-inline-handling)
2. Receiving keys from a GPG key server.
   [Try it!]({{site.baseurl}}/#receiving-from-a-key-server)
3. Manually downloading a GPG key file.
   [Try it!]({{site.baseurl}}/#manual-download)

After you obtain my public key, it's highly relevant that you verify
the authenticity of the key by
[checking its fingerprint]({{site.baseurl}}/#checking-fingerprint).

You might want to know that my GPG key is of type 2048-bit RSA, was
generated on 2013-01-12 and won't expire.  Its fingerprint is `7CB1
208C 7336 56B7 5962  2500 27B9 C6FD 28D6 18AF`.


#### Browser inline handling

If you are using a browser which supports handling GPG inline content,
such as Mozilla-based browsers with the
[WebPG](https://addons.mozilla.org/en-US/firefox/addon/webpg-firefox/)
add-on, you can easily add my public GPG key in-lined below to your
key-ring.  Note that for this to work you need to enable inline
formatting of GPG messages and keys.

<pre id="inline-gpg">
{% include oitofelix.gpg %}
</pre>


#### Receiving from a key server

My public GPG key can be found at
[hkp://keys.gnupg.net/](hkp://keys.gnupg.net/) and its ID is
`0x28D618AF`.  You can retrieve it by the following command:

<pre>
$ gpg --recv-keys 0x28D618AF --keyserver hkp://keys.gnupg.net/
</pre>


#### Manual download

Download my armored public [GPG key](oitofelix.gpg) from this server
and then import it to your public key-ring using:

<pre>
$ gpg --import oitofelix.gpg
</pre>


#### Checking fingerprint

To verify the authenticity of the key you've imported to your public
key-ring, enter the command:

<pre>
$ gpg --fingerprint 0x28D618AF | sed -n '/^[[:blank:]]\+Key/s/^.*= //p'
</pre>

It must print the following fingerprint: `7CB1 208C 7336 56B7
5962  2500 27B9 C6FD 28D6 18AF`.

Otherwise something is wrong!  In that case <strong>don't</strong> use
the retrieved key to verify signatures or encrypt data, and contact
me.


### SSH key

You can use my public SSH key (2048-bit RSA) for granting me
access to any computer you have an user account in and are allowed to
make SSH connections to.  To do that, follow the steps below logged in
the system as the user you want to grant me access to.

First download [my public SSH key](/oitofelix.ssh) and verify the
authenticity of the key by running:

<pre>
$ ssh-keygen -lf oitofelix.ssh | cut -f2 -d' '
</pre>

It must print the following fingerprint:
`c6:11:b0:09:0d:b7:0e:4b:49:d1:36:88:da:33:a3:6e`.  Otherwise
something is wrong!  In that case __abort__ the procedure
at this step and contact me.

If the fingerprint is valid, you can safely add the key to your list
of authorized SSH keys by issuing the following command:

<pre>
$ cat oitofelix.ssh >> ~/.ssh/authorized_keys
</pre>

It's done!  Contact me so we can proceed with the remote assistance.


</div>
