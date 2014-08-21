What is Syncany?
================

Syncany is an open source Dropbox-like file sync tool. It synchronizes files and folders between computers either manually or automatically. Users can define certain folders on their machine and keep them in sync with friends or colleagues. 

So what makes Syncany **awesome**?

* Automatic/continuous file synchronization
* Use-your-own storage (FTP, S3, WebDAV, NFS, Samba/Windows file share, ...)
* Files are encrypted before upload (don't trust anybody but yourself)
* Files are `deduplicated <http://en.wikipedia.org/wiki/Data_deduplication>`_ locally (massive space savings on remote storage)
* Files are intelligently versioned (restoring old versions or deleted files is easy)

**Excited yet? Ready to learn more?**

.. image:: _static/what_is_syncany_overview.png
   :align: center

Syncany takes the idea of a Dropbox-like continuous file synchronization tool and applies it to the real world: It makes use of the storage that is *available* rather than being bound to a certain protocol or backend a certain provider is offering. **With a simple plugin-based storage system, Syncany can turn almost anything into a usable backend storage**. Right now, it can use folders on an FTP or SFTP storage, WebDAV or Samba shares and Amazon S3 buckets, but that's just the beginning. Because it's so easy to implement plugins, more are definitely coming. Even things like using IMAP folders or Flickr's free 1 TB of image data could be used to store your data.

Besides its incredible flexibilty in terms of storage, Syncany is also a very privacy-aware software: **User data never leaves the local machine without being encrypted**. Data confidentiality and user privacy are the taken very seriously -- 128-bit AES+Twofish/GCM encryption is built-in by default.

Combining these two features makes Syncany really awesome: You can use all of the free storage that the Internet gives you (Google Drive, OneDrive, etc.) to share your files, but you don't have to worry about your privacy. Syncany takes care of encryption before files are uploaded.

Target audience: Who needs it?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The target audience for Syncany is not the usual *cloud user*, but rather at the more privacy-aware user. xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

Syncany is is for those out there that don't trust the providers of online storage with their data. For people that are afraid of what sysadmins and other interested parties might do with their data. And it's for people who would love to use all the free storage that the Internet provides without having to give up to any privacy. 

Use cases:

* Continuous file synchronization
* Interval-based or on-demand backups 
* Simple binary-compatible file versioning

What Syncany is **not**
^^^^^^^^^^^^^^^^^^^^^^^
* A service. You don't pay for it. You don't get storage from us. 
* Usable for critical files yet. It's alpha software. Don't do it!
* A large network of interconnected machines. You can't share folders with strangers. You must trust the persons you share files with.
* A fully fledged version control system. 


Requirements: What do I need?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Do you have some spare storage you 
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx


Use Case 1: Friends sharing files 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Pim wants to share some ideas with Philipp, and Philipp wants to share some pictures with Steffen. Pim has a Windows server running a Samba server (Windows share), and Philipp has has a virtual server from a random hosting company lying around -- all set up with a spare SFTP account. 

.. image:: _static/what_is_syncany_use_case_1.png
   :align: center
   
Pim sets up a Syncany shared folder with Philipp, using the shared Windows folder on his server as a backend storage. He uses the ``sy init`` command to do that, types in ``samba`` to use the Windows share plugin, and chooses a strong password to encrypt the data with. After the one-minute setup, he gets a syncany://-link from Syncany. This link contains all the information required to access the storage. Philipp can now use this and the password to access the Syncany folder (using the ``sy connect`` command). Since the everything that lands in the *cloud* is encrypted with a key derived from the password, Pim and Philipp don't have to worry about a nosy storage provider or other interested parties.

The process between Philipp and Steffen is exactly the same, only that now Philipp initializes the repository on his own remote storage, and that the SFTP plugin is used. 

Use Case 2: Sharing in a company
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

With server + web interface