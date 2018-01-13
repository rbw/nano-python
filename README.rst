RaiBlocks Python Library
========================

.. image:: https://travis-ci.org/dourvaris/raiblocks-py.svg?branch=1.0.0rc1
    :target: https://travis-ci.org/dourvaris/raiblocks-py

.. image:: https://github.com/dourvaris/raiblocks-py/raw/master/coverage.svg?sanitize=true

.. image:: https://img.shields.io/pypi/pyversions/raiblocks.svg?style=flat-square

.. image:: https://img.shields.io/pypi/l/raiblocks.svg

This library contains a python wrapper for the RaiBlocks RPC server
which tries to make it a little easier to work with by converting RPC responses
to native python ones and exposing a pythonic api for making RPC calls.

Also included are utilities such as converting rai/xrb and interesting accounts


Installation
------------

.. code-block:: text

    pip install raiblocks


RPC client
----------

.. code-block:: python

    >>> from raiblocks import RPCClient
    >>> rpc = RPCClient('http://localhost:7076')
    >>> rpc.version()
    {
        'rpc_version': 1,
        'store_version': 10,
        'node_vendor': 'RaiBlocks 9.0'
    }
    >>> rpc.peers()
    {
        '[::ffff:75.171.168.5]:7075': 4,
        '[::ffff:108.44.38.183]:1032': 4
    }

A full list of available methods can be found in :doc:`/rpc/index`


Conversion
----------

.. code-block:: python

    >>> from raiblocks import convert
    >>> convert(12, from_unit='XRB', to_unit='raw')
    Decimal('1.2E+31')

    >>> converter(0.4, from_unit='krai', to_unit='XRB')
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    ValueError: float values can lead to unexpected
    precision loss, please use a Decimal or string
    eg. converter('0.4', 'krai', 'XRB')

    >>> convert('0.4', from_unit='krai', to_unit='XRB')
    Decimal('0.0004')


Known Accounts / Constants
--------------------------

.. code-block:: python

    >>> from raiblocks import GENESIS_BLOCK_HASH
    >>> GENESIS_BLOCK_HASH
    '991CF190094C00F0B68E2E5F75F6BEE95A2E0BD93CEAA4A6734DB9F19B728948'


.. code-block:: python

    >>> from raiblocks import KNOWN_ACCOUNT_IDS
    >>> KNOWN_ACCOUNT_IDS['xrb_1ipx847tk8o46pwxt5qjdbncjqcbwcc1rrmqnkztrfjy5k7z4imsrata9est']
    'Developer Fund'


.. code-block:: python

    >>> from raiblocks import KNOWN_ACCOUNT_NAMES
    >>> KNOWN_ACCOUNT_NAMES['Burn']
    'xrb_1111111111111111111111111111111111111111111111111111hifc8npp'