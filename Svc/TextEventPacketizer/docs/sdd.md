# Svc::TextEventPacketizer Component

## 1. Introduction

The `Svc::TextEventPacketizer` component processes _textual_ events from other components via their LogText ports. This is the only difference compared to the [Svc::ActiveLogger](../../ActiveLogger/docs/sdd.md) component which is the default event logger in Fprime deployments. 

The events are put in packets and sent to an external component like the ground interface. The component provides event filtering capability such that events may be turned off via ID or severity.

## 2. Requirements

The requirements for `Svc::TextEventPacketizer` are as follows:

Requirement | Description | Verification Method
----------- | ----------- | -------------------
EP-001 | The `Svc::TextEventPacketizer` component shall have the same interfaces as `Svc::ActiveLogger` except for LogText input events instead of Log. | Inspection; Test
EP-002 | The `Svc::TextEventPacketizer` component's output packet shall replace the LogPacket field in the output packet with the severity (as FwEnumStoreType) and the text event (as a fixed size string, without prepended size field). | Test
EP-003 | The `Svc::TextEventPacketizer` component shall otherwise (i.e. wherever EP-001 and EP-002 do not apply) be identical to Svc::ActiveLogger in behaviour. | Test

#### 3.1.2 Ports

The `Svc::TextEventPacketizer` component uses the following port types:

Port Data Type | Name | Direction | Kind | Usage
-------------- | ---- | --------- | ---- | -----
[`Fw::LogText`](../../../Fw/Log/docs/sdd.md) | LogRecv | Input | Synchronous | Receive _textual_ events from components
[`Fw::Com`](../../../Fw/Log/docs/sdd.md) | PktSend | Output | n/a | Send event packets to external user
[`Svc::FatalEvent`](../../../Svc/Fatal/docs/sdd.md) | FatalAnnounce | Output | n/a | Send FATAL event (to health)

## 5. Unit Testing

Unit tests are not yet done for this component. It is believed to be low-risk given the similarity with ActiveLogger.

## 6. Change Log

Date | Description
---- | -----------
04/03/2025 | First version



