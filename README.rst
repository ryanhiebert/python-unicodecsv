unicodecsv
==========

The unicodecsv is a drop-in replacement for Python 2's csv module which supports unicode strings without a hassle.

More fully
----------

Python 2's csv module doesn't easily deal with unicode strings, leading to the dreaded "'ascii' codec can't encode characters in position ..." exception.

You can work around it by encoding everything just before calling write (or just after read), but why not add support to the serializer?

.. code-block:: pycon

   >>> import unicodecsv as csv
   >>> from io import BytesIO
   >>> f = BytesIO()
   >>> w = csv.writer(f, encoding='utf-8')
   >>> _ = w.writerow((u'é', u'ñ'))
   >>> _ = f.seek(0)
   >>> r = csv.reader(f, encoding='utf-8')
   >>> next(r) == [u'é', u'ñ']
   True
