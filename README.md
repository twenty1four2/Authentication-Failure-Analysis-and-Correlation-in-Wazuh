## Screenshots
<img width="1897" height="959" alt="escalatedbruteforceevent" src="https://github.com/user-attachments/assets/47500075-ea54-474d-9ca2-b9f2eeb1ddcd" />
<img width="799" height="499" alt="bruteforcediffusers" src="https://github.com/user-attachments/assets/f87b127f-6b85-46a0-8bf2-7f903c527f4f" />

Authentication Failure Analysis and Correlation in Wazuh
Overview

This lab focuses on analyzing repeated authentication failures in a Wazuh SIEM/XDR environment and determining when activity transitions from a false positive to a true positive. The goal was to simulate real SOC decision-making by evaluating alert volume, time-based patterns, and authentication outcomes rather than treating alerts at face value.

The lab emphasizes investigation, correlation, and escalation logic commonly used by SOC analysts when handling authentication-related alerts.

Lab Environment

Wazuh Manager (Linux)

Wazuh Dashboard

Linux endpoint (VirtualBox)

Windows endpoint with Wazuh agent installed

Internal network traffic only (home lab)

Objectives

Identify repeated authentication failure events in Wazuh

Distinguish false positives from true positives based on frequency and timing

Correlate failed authentication attempts with successful logins

Observe alert escalation behavior in Wazuh

Practice SOC-style investigation and documentation

Attack Simulation

To generate authentication failure events, multiple failed login attempts were intentionally performed using non-existent or incorrect usernames over a short time window. These attempts originated from an internal IP address to simulate a realistic internal user scenario.

As the number of failures increased within a condensed timeframe, Wazuh escalated the alert severity, eventually triggering a “Multiple Authentication Failures” rule.

Investigation Process

Reviewed authentication failure events in the Wazuh Threat Hunting dashboard

Filtered events by authentication failure rule groups

Analyzed timestamps to identify rapid, repeated attempts

Reviewed source IP addresses to confirm internal origin

Correlated failed attempts with subsequent successful authentication events

Determined whether escalation criteria justified a true positive classification

Findings

Initial authentication failures were classified as a false positive due to low volume and internal source IP

As failures increased rapidly within a short time window, alert severity escalated

Correlation with authentication success confirmed continued account access

Despite internal origin, the frequency of attempts justified further monitoring

Final classification shifted to a true positive requiring investigation rather than immediate containment

Key Takeaways

Not all authentication failures are malicious by default

Time-based correlation is critical in alert triage

Internal IP addresses do not automatically mean benign activity

Alert tuning plays a major role in preventing false positives and false negatives

Context and patterns matter more than single events

Skills Demonstrated

SIEM investigation and alert triage

Authentication log analysis

Event correlation and escalation logic

False positive vs true positive classification

SOC-style documentation and reporting

Wazuh Threat Hunting usage

Notes

All IP addresses and events shown originate from an isolated home lab environment. No production systems or real user data were involved.
