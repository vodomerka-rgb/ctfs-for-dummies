---
layout: post
title: Diffie-Hellman Key Exchange
date: 2026-06-11
permalink: /posts/dhke
---

# Diffie-Hellman Key Exchange:
## Quick info:
Name: creators’ last names
Created: 1976
Type: Symmetric
Considered secure: Yes

## Background:
The Diffie-Hellman key exchange is a method used to generate secret keys with another party over unsecured networks. Because of the nature of the protocol, even if traffic regarding the generation of the key is intercepted, the key cannot be calculated by an outside party. However there are post-quantum limitations.

## Procedure:
In our scenario, we will have two people, Alice and Bob (for A and B).

1. Together they generate a prime number *p* and a number *g* which is coprime to p-1. This can be shared.
2. Alice generates a secret prime number $$a$$ and calculates a value we can call $$A = g^a \bmod p$$. She sends $$A$$ to Bob.
3. Bob does the same thing. He generates a secret prime number $$b$$ and sends Alice $$B = g^b \bmod p$$.
4. Then, Alice and Bob do the same exact procedure on the number they got. So Alice does $$B^a \bmod p$$ and Bob does $$A^b  \bmod p$$. And that number is their shared key.

## Why does it work?
Recall that $$A = g^a \bmod p$$. This means that $$A^b  \bmod p$$ is the same as $$(g^a \bmod p)^b \bmod p$$. This, in turn, becomes $$g^{ab}\bmod p$$, because $$(g^a)^b = g^{ab}$$. 

The other expression, $$B^a \bmod p$$, becomes $$(g^b \bmod p)^a \bmod p$$, which is then the same as the previous one: $$g^{ba}\bmod p$$ or $$g^{ab}\bmod p$$. 

So, Alice and Bob end up calculating the same number. 

But, if all of the values involved in the calculation except a and b could be intercepted, shouldn’t this be insecure? Well, no. Actually, finding $$g^{ab}\bmod p$$ from the known values of p, g, $$g^{a}\bmod p$$, and $$g^{b}\bmod p$$ would take an unreasonably long time to compute with any known classical algorithm. However, quantum computing could change that. For now though, the process is still considered safe. 

## Uses:
It could be used alone for symmetric encryption, or for algorithms that require shared secrets, like AES. 

Many extensions have been invented off the base of this protocol, including Elliptic Curve Diffie-Hellman (ECDH), Diffie-Hellman Ephemeral (DHE), ECDHE (Elliptic Curve Diffie-Hellman Ephemeral), Triple Diffie–Hellman (3-DH), and Extended Triple Diffie–Hellman (X3DH).  
